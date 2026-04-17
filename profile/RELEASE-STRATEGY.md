
## Release Strategy

EOEPCA+ is formally released via the [Deployment Guide](https://eoepca.readthedocs.io/projects/deploy/en/latest/), which baselines a set of Building Blocks versions that are validated as a coherent integration.

### Well Supported and Actively Maintained

EOEPCA+ releases are well supported and actively maintained by the development teams.

The development teams curate, validate, and sustain each repository release baseline over time.

Thus, an EOEPCA+ release represents a coherent validated set that comprises the following artifacts:

- Deployment Guide:
  - `docs/`: deployment guidance published via Read the Docs.
  - `scripts/`: helper automation used to deploy EOEPCA+ Building Blocks and related release artifacts.
  - `notebooks/`: executable validation and demonstration notebooks aligned with the documented deployment behavior.
- Tutorials (validation)<br>
  Configured in `EOEPCA/eoepca-killercoda`: scenario-driven hands-on flows that should match the same release capabilities.

For each tagged release, these artifacts are expected to describe and validate the same EOEPCA+ platform behavior.

### Version Numbering

Releases follow Semantic Versioning for version semantics, with repository tags in the form `eoepca-MAJOR.MINOR` (optionally `eoepca-MAJOR.MINOR.PATCH` when patch granularity is required).

Human-readable release labels map directly to this tag namespace. For example, `Release 2.0` corresponds to git tag `eoepca-2.0`.

- `MAJOR`: reserved for governance-level exceptional release boundaries, typically driven by significant architecture change or contractual/programmatic phasing.<br>
  Typical triggers include:
    - Platform architecture transitions that redefine how EOEPCA+ is composed or operated.
    - Contractual/programmatic phase transitions that require a clearly separated release line.
    - Broad migration expectations across multiple Building Blocks and dependent artifacts.
    - Intentional reset of compatibility expectations at EOEPCA+ release level.

- `MINOR`: new features/use-cases/components that do not meet `MAJOR` criteria.<br>
  Typical triggers include:
    - New Building Blocks, new features/use-cases, or new deployment paths
    - Integration of sub-component feature releases where `MAJOR` criteria are not met.
    - Material operational improvements and release rollups outside pure fix-only scope.
    - Changes that may require limited migration, where architecture/programmatic `MAJOR` criteria are not met.
    - Significant new guidance enabling new supported usage patterns.

- `PATCH`: backward-compatible corrections without capability expansion, including backward-compatible security vulnerability fixes.<br>
  Typical triggers include:
    - Script fixes, reliability/stability fixes, and safe configuration corrections.
    - Backward-compatible security vulnerability fixes (for example dependency patches, CVE remediations, and hardening with no required migration).
    - Documentation corrections and clarification updates.
    - Backward-compatible sub-component bugfix rollups.

Because this repository is the umbrella release vehicle for EOEPCA+, release numbering is decided at repository level, not per single sub-component or artifact.

`MAJOR` is not an automatic outcome of a single breaking change in one component; it is an explicit release decision at EOEPCA+ program level.

For routine rollups, use this default rule:

- If release scope is limited to backward-compatible fixes/clarifications, the repository release is `PATCH`.
- Else, if release scope introduces new features/use cases/components but does not meet `MAJOR` criteria, the repository release is `MINOR`.
- Escalate to `MAJOR` only when architecture or contractual phasing criteria are met.

Security note: classify vulnerability fixes as `PATCH` when backward-compatible; if mitigation requires broader behavioral change or migration, classify as `MINOR` unless `MAJOR` criteria are met.

Pre-releases should use standard SemVer pre-release suffixes in the same namespace, for example `eoepca-2.1.0-rc.1`.

### Release Cycle

EOEPCA+ release operations are maintained by the development teams to provide a well supported and actively maintained release line.

`PATCH` releases are produced at least quarterly as fix rollups for backward-compatible corrections and hardening updates.

`MINOR` releases do not follow a fixed timeline; they are issued when a stable set of updates is ready to be consolidated into a coherent release.

Each release is prepared by establishing a baseline for the composing Building Blocks (BBs), similar to a feature-freeze point.

- Baseline definition: record the BB versions/commits and associated deployment assumptions that form the intended release candidate.
- Delta assessment: compare this baseline with the previous EOEPCA+ release baseline to identify the required update set.
- Rollup selection: include only the validated and release-ready subset of BB developments in the repository release.
