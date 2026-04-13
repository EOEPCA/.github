# EOEPCA+ Building-Block Security Best Practice

These practices are aimed at:
* enabling baseline vulnerability management practices within operators' clusters,
* enabling EOEPCA components to be used in clusters with certain security rules, such as Terrabyte's rule on not running as root, and improving the security of  Kubernetes configuration,
* reducing vulnerabilities present in EOEPCA releases.


Operators are ultimately responsible for their cluster security, including running a vulnerability scanner, upgrading vulnerable software and establishing secure Kubernetes configuration according to their policies. However, the EOEPCA project should:
* Reduce the vulnerabilities and weak configuration operators have to deal with.
* Ensure that operators can detect and respond to vulnerabilities stemming from EOEPCA BBs, and from EOEPCA Helm charts and the Deployment Guide.

**Table of Contents**

- [EOEPCA+ Building-Block Security Best Practice](#eoepca-building-block-security-best-practice)
  - [For Individual BBs](#for-individual-bbs)
    - [Kubernetes Configuration](#kubernetes-configuration)
      - [Weak Container Configuration](#weak-container-configuration)
      - [Image Tags](#image-tags)
      - [Vulnerable Images](#vulnerable-images)
    - [Docker Images](#docker-images)
      - [Build-time Scanning](#build-time-scanning)
      - [Container Hygiene and Updates](#container-hygiene-and-updates)
      - [Software Installation Method](#software-installation-method)
    - [Software](#software)
      - [Versioning](#versioning)
      - [Version Pinning](#version-pinning)
      - [Dependency Vulnerability Management](#dependency-vulnerability-management)
      - [Security Policy and Alerts](#security-policy-and-alerts)
      - [Security Advisories](#security-advisories)
  - [For EOEPCA Releases](#for-eoepca-releases)
      - [Weak Kubernetes Configuration](#weak-kubernetes-configuration)
      - [Vulnerable Packages](#vulnerable-packages)
      - [Security Scanner Deployment](#security-scanner-deployment)


## For Individual BBs

This applies to Kubernetes configuration in EOEPCA-managed Helm charts or which is generated directly by BBs.
### Kubernetes Configuration

#### Weak Container Configuration

Weak configuration detected by Trivy can be seen at https://github.com/EOEPCA/helm-charts-dev/security/code-scanning . The dev cluster is also scanned and the results are available as CRs which can be viewed with, for example, `kubectl get configauditreports --all-namespaces -o wide`

BB developers should attempt to address the alerts for any EOEPCA chart they're responsible for (or any other Kubernetes configuration from their BB). Alerts in helm-charts-dev can be ignored by adding to .trivyignore.yaml if the configuration that has generated them is essential to the component. This may mean that some operators will be unable to use it and should be rare.

Some particular practices that should be followed but are mostly currently not are:
* A securityContext should be applied to all containers (including init containers) which specifies:
	* `runAsNonRoot: true` - some operators will not be able to use your component at all if it uses root. `runAsUser` may be required if the image defaults to using root.
	* `allowPrivilegeEscalation: false`
	* `readOnlyRootFilesystem: true` - additional volumes may need to be added
* Except for ingress providers and similar, containers should not use privileged ports.
* Images should come from a well-known registry. This might not be recognized by the scanner if they rely on docker.io being default (which, rarely, can vary between clusters or container runtimes), so image names may need to be fully qualified (eg `docker.io/library/busybox` instead of just `busybox`).

The dev cluster's scanner is unable to filter results correctly. Most results that would be filtered are not in EOEPCA BBs, but the lack of a seccomp profile of RuntimeDefault will be shown and can be ignored (the effect of this can vary across clusters, it will be difficult to verify correct functioning and operators can apply it as a default for their cluster themselves anyway).

#### Image Tags

Image versions should be pinned (not `latest`, for example) and operators should be able to reconfigure the version of any image deployed by an EOEPCA Helm chart through the values file. This allows them to upgrade them in a controlled way if a vulnerability is detected.

#### Vulnerable Images

The default tags specified for images (EOEPCA or third-party) referenced in Helm charts or BB configs should not be versions with known vulnerabilities. This should be true at the point of an EOEPCA release, operators are expected to upgrade versions themselves in between releases.


### Docker Images

These apply to EOEPCA-maintained Docker images
#### Build-time Scanning

Images should be scanned for vulnerabilities and weak configuration. An example with Trivy can be seen at https://github.com/ahaywardtvuk/registration-harvester/blob/main/.github/workflows/build-publish-image.yml , which adds the following to the build Action and will result in alerts being added to the 'security' tab:

```
      #... existing steps up to and including
      - name: Build and push
        id: build
        uses: docker/build-push-action@v6
        with:          
          push: true
          tags: ${{ steps.meta.outputs.tags }}

      # New steps
      - name: Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@0.35.0
        with:
          image-ref: ${{ steps.print-tags.outputs.tag }}
          scan-type: image
          trivy-config: trivy-config.yaml
          
      - name: Upload Trivy scan results to GitHub Security tab
        uses: github/codeql-action/upload-sarif@v4
        with:
          sarif_file: 'trivy-results.sarif'
```

with `trivy-config.yaml`:

```
format: 'sarif'
output: 'trivy-results.sarif'
severity: 'CRITICAL,HIGH,MEDIUM,UNKNOWN'
exit-code: 0
ignorefile: .trivyignore.yaml
scan:
  scanners:
    - vuln
    - misconfig
    - secret
```

It can then also be run locally with `trivy image --config trivy-config.yaml  --output /dev/stdout --format table`

Zero alerts for misconfiguration and secrets should be aimed for but will often not be practical for vulnerabilities due to the large amount of unused code and unexposed interfaces in many images (see next item).
#### Container Hygiene and Updates

A very large number of vulnerabilities are detected within the images in the cluster because many EOEPCA-published images contain a lot more files than required and/or use old versions of base images. Whilst many are not genuine vulnerabilities they still make it very difficult for operators and maintainers to identify those which need action.

To reduce this, image maintainers should update base images regularly and reduce the amount of unnecessary files included in them. Using smaller base images and using multi-stage builds can both help with this. For example, the multi-stage Python build at https://github.com/ahaywardtvuk/registration-harvester/blob/trivy-scanning/Dockerfile reduces the number of detected non-Python vulnerabilities from 203 to 3 due to the removal of build-essential (gcc, etc.) and Git from the image.

#### Software Installation Method

Software, including BB code itself, should be installed into images in a way that allows scanners like Trivy to recognize it and its version. For example, the registration harvester Dockerfile at https://github.com/EOEPCA/registration-harvester/blob/0c93b63ef63a1b4ef9ca957f5d331b4a7fb10ede/Dockerfile allows this because it installs the harvester package with pip (`COPY . /worker`, 
`RUN python -m pip install --no-cache-dir --upgrade /worker`)

Many other images copy source code directly meaning that no package name and version can be found. If a security advisory is later issued for the BB itself then operators will not be alerted by their scanners that they have the vulnerable version installed.

### Software

These apply to EOEPCA-maintained software packages, meaning the source code and any binaries but not Docker images.

#### Versioning

EOEPCA BB releases should have well-defined versions which are reliably transposed into package metadata (eg, Git tag or GitHub release always match the version in pyproject.toml, or the package version is auto-generated with a tool like setuptools-git-versioning or one like Hatch).  A user of the BB releases should be able to reliably tell exactly which code they have and if they have a vulnerable version.

#### Version Pinning

Dependencies of applications (but not libraries intended for incorporation into other applications) should be fully resolved and pinned with a typical ecosystem-specific method, for example with `uv lock` or a PEP 751 lock file for Python. This ensures that builds are repeatable and that the dependencies scanned by vulnerability management tools match those installed into real environments.

#### Dependency Vulnerability Management

The dependency lock file should be scanned for known vulnerabilities, for example with Dependabot or pip-audit.  For tools like pip-audit, it should run on a schedule (eg, weekly) to detect newly-discovered vulnerabilities and during at least release builds.

Whilst vulnerabilities should also be detected by image scanners, language-specific tools are more accurate and can run on non-image builds for faster detection. Unlike image scanners, we should aim for zero detected vulnerabilities with alerts always being individually assessed for impact (and added to an ignore file if appropriate).

Operators are not expected to rebuild EOEPCA BBs and new versions should be released promptly to upgrade vulnerable dependencies, not only at the next EOEPCA release point.
#### Security Policy and Alerts

EOEPCA BBs should have a security policy in SECURITY.md but this can be very simple (for example, see https://github.com/geopython/pycsw/blob/master/SECURITY.md). This should specify a private way to report vulnerabilities and which versions have security support (which may be just the most recent). Private reporting can be enabled via GitHub in the repository settings, under 'Advanced Security' -> 'Private vulnerability reporting'.

#### Security Advisories

If you discover or receive a report of security vulnerability in your code then, once a fix has been published, you should ensure that operators' scanning tools will alert them by creating a security advisory and CVE ID. This can be done via GitHub as documented at https://docs.github.com/en/code-security/how-tos/report-and-fix-vulnerabilities/fix-reported-vulnerabilities/creating-a-repository-security-advisory

## For EOEPCA Releases

#### Weak Kubernetes Configuration

The result of following the deployment guide should not include weak Kubernetes configuration as described above.

#### Vulnerable Packages

At the point of an EOEPCA release, the deployment guide should not install vulnerable versions of any software, whether an EOEPCA BB or third-party. This should be checked by following the guide and running the Trivy Kubernetes scanner against the results, using the same settings as used in the dev cluster.

#### Security Scanner Deployment

The deployment guide should include the installation of Trivy and a recommended configuration (but operators may use an alternative like Neuvector). It should explain that operators are responsible for finding and upgrading vulnerable package versions between releases.
