
# EO Exploitation Platform Common Architecture

Architecture and software building-blocks for data exploitation and platform interoperability.

## Overview

Earth Observation (EO) data has quickly evolved into an indispensable resource, directly facilitating solutions for society's most pressing challenges. This intensifying influx of data, oftentimes distributed across multiple independent platforms, presents a significant challenge for end-users in efficiently accessing and collaborating on critical geospatial tasks. Nevertheless, these platforms are more commonly collocated with cloud computing resources and applications such that users are now able to perform geospatial analysis tasks remotely. Working in the cloud bypasses traditional download, storage and performance limitations, however the distributed nature of these platform networks introduces complexities in the free and collective access to this remote geospatial data.

Our vision with EOEPCA then is for greater interoperability between such platforms, towards an open network of resources, whilst enabling current and future users to easily collaborate on geospatial analysis tasks at source. To this end we are helping to establish a consensus of best practice for EO Exploitation Platforms, based on open standards. Supporting that, we are developing a reference implementation of building blocks, as free open source software.

The goal of the EOEPCA's “Common Architecture” is therefore to define and agree the technical interfaces for the future exploitation of Earth Observation data in a distributed environment. The Common Architecture will provide the interfaces to facilitate the federation of different EO resources into a “Network of EO Resources”. The “Common Architecture” will be defined using open interfaces that link the different Resource Servers (building blocks) so that a user can efficiently access and consume the disparate services of the “Network of EO Resources”.

## Quick Links

System...
* [**EOEPCA Release v1.4** - https://github.com/EOEPCA/eoepca/releases/tag/v1.4](https://github.com/EOEPCA/eoepca/releases/tag/v1.4)
* [**Deployment Guide** - https://deployment-guide.docs.eoepca.org/v1.4/](https://deployment-guide.docs.eoepca.org/v1.4/)
* [**Helm Charts** - https://eoepca.github.io/helm-charts](https://eoepca.github.io/helm-charts) [\[sources\]](https://github.com/EOEPCA/helm-charts)

Building Blocks...
* [**ADES - ZOO-Project DRU (Application Deployment & Execution Service)**](https://github.com/ZOO-Project/ZOO-Project) - [[repository]](https://github.com/ZOO-Project/ZOO-Project) [[docs]](https://www.zoo-project.org/new/Resources/Documentation):
  * [**Helm chart**](https://github.com/ZOO-Project/charts/tree/main/zoo-project-dru)
  * [**eoepca-proc-service-template**](https://github.com/EOEPCA/eoepca-proc-service-template) - Cookie-cutter template for Application Package execution in Kubernetes
  * [**zoo-calrissian-runner**](https://github.com/EOEPCA/zoo-calrissian-runner) - Python library used by the `eoepca-proc-service-template` to aid orchestration of CWL application packages running in Kubernetes via Calrissian
  * [**pycalrissian**](https://github.com/terradue/pycalrissian) - Python library used by `zoo-calrissian-runner` to aid interfacing with Calrissian and Kubernetes
* [**Application Hub**](https://github.com/EOEPCA/application-hub-chart) - [[repository]](https://github.com/EOEPCA/application-hub-context) [[docs]](https://eoepca.github.io/application-hub-context/):
  * **ApplicationHub Applications:**
    * **Processor Development Environment** [[repository]](https://github.com/EOEPCA/pde-code-server)
    * **JupyterLab** [[repository]](https://github.com/EOEPCA/iat-jupyterlab)
    * **Remote Desktop** [[repository]](https://github.com/EOEPCA/iga-remote-desktop)
    * **Remote Desktop with QGIS** [[repository]](https://github.com/EOEPCA/iga-remote-desktop-qgis)
    * **Remote Desktop with SNAP** [[repository]](https://github.com/EOEPCA/iga-remote-desktop-snap)
    * **Dashboard with Streamlit** [[repository]](https://github.com/EOEPCA/iga-streamlit-demo)
* [**Resource Catalogue**](https://github.com/EOEPCA/rm-resource-catalogue) - [[repository]](https://github.com/geopython/pycsw) - [[docs]](https://github.com/EOEPCA/rm-resource-catalogue)
* [**Data Access**](https://github.com/EOEPCA/rm-data-access/) - [[repository]](https://gitlab.eox.at/vs/vs) - [[docs]](https://github.com/EOEPCA/rm-data-access/)
* [**Registration API**](https://github.com/EOEPCA/rm-registration-api) - [[repository]](https://github.com/EOEPCA/rm-registration-api) - [[docs]](https://github.com/EOEPCA/rm-registration-api/wiki)
* [**Workspace API**](https://github.com/EOEPCA/rm-workspace-api/) - [[repository]](https://github.com/EOEPCA/rm-workspace-api) - [[docs]](https://github.com/EOEPCA/rm-workspace-api/wiki)
* [**Minio Bucket API**](https://github.com/EOEPCA/rm-minio-bucket-api) - [repository](https://github.com/EOEPCA/rm-minio-bucket-api) - [docs](https://github.com/EOEPCA/rm-minio-bucket-api#readme)
* **Identity & Access Management...**
  * **Keycloak Solution (NEW)**
    * [**Identity Service**](https://github.com/EOEPCA/um-identity-service) - [[repository]](https://github.com/EOEPCA/um-identity-service) - [[docs]](https://deployment-guide.docs.eoepca.org/v1.4/eoepca/identity-service/) - [[keycloak]](https://www.keycloak.org/documentation)
    * [**Identity API**](https://github.com/EOEPCA/um-identity-api) - [[repository]](https://github.com/EOEPCA/um-identity-api) - [[docs]](https://deployment-guide.docs.eoepca.org/v1.4/eoepca/identity-service/)
    * [**Identity Gatekeeper**](https://github.com/gogatekeeper/gatekeeper) - [[repository]](https://github.com/gogatekeeper/gatekeeper) - [[docs]](https://deployment-guide.docs.eoepca.org/v1.4/eoepca/resource-protection-keycloak/) - [[gogatekeeper]](https://gogatekeeper.github.io/gatekeeper/userguide/)
  * **Gluu Solution (deprecated)**
    * [**Login Service**](https://github.com/EOEPCA/um-login-service) - [[repository]](https://github.com/EOEPCA/um-login-service) - [[docs]](https://github.com/EOEPCA/um-login-service/wiki) - [[gluu]](https://gluu.org/docs/gluu-server/4.1/)
    * [**Resource Protection**](https://system-description.docs.eoepca.org/current/iam/resource-guard/) - [[repository]](https://github.com/EOEPCA/helm-charts/tree/main/charts/resource-guard) - [[docs]](https://github.com/EOEPCA/helm-charts/tree/main/charts/resource-guard#readme)
    * [**Policy Decision Point**](https://github.com/EOEPCA/um-pdp-engine) - [[repository]](https://github.com/EOEPCA/um-pdp-engine) - [[docs]](https://github.com/EOEPCA/um-pdp-engine/wiki)
    * [**User Profile**](https://github.com/EOEPCA/um-user-profile) - [[repository]](https://github.com/EOEPCA/um-user-profile) - [[docs]](https://github.com/EOEPCA/um-user-profile/wiki)
