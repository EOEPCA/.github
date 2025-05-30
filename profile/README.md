
# EOEPCA+ - EO Exploitation Platform Common Architecture

Architecture and software building-blocks for data exploitation and platform interoperability.

* **EOEPCA+ (Phase 2)**<br>
  EOEPCA+ represents Phase 2 of the project which takes a fresh appraisal of the architecture, the building-blocks, their capabilities, and their implementation approach. Thus, EOEPCA+ represents a major refactor of the Reference Implementation.<br>
  The latest public release of EOEPCA+ is [**Release 2.0-rc1**](https://github.com/EOEPCA/eoepca-plus/releases/tag/2.0-rc1) - see associated [Deployment Guide](https://eoepca.readthedocs.io/projects/deploy/en/2.0-rc1/).

* **EOEPCA (Phase 1)**<br>
  The original EOEPCA project concluded with [**Release 1.4**](https://github.com/EOEPCA/eoepca/releases/tag/v1.4), ([Deployment Guide](https://eoepca.readthedocs.io/projects/deploy/en/v1.4-stable/)).

---

## Overview

Earth Observation (EO) data has quickly evolved into an indispensable resource, directly facilitating solutions for society's most pressing challenges. This intensifying influx of data, oftentimes distributed across multiple independent platforms, presents a significant challenge for end-users in efficiently accessing and collaborating on critical geospatial tasks. Nevertheless, these platforms are more commonly collocated with cloud computing resources and applications such that users are now able to perform geospatial analysis tasks remotely. Working in the cloud bypasses traditional download, storage and performance limitations, however the distributed nature of these platform networks introduces complexities in the free and collective access to this remote geospatial data.

Our vision with EOEPCA+ then is for greater interoperability between such platforms, towards an open network of resources, whilst enabling current and future users to easily collaborate on geospatial analysis tasks at source. To this end we are helping to establish a consensus of best practice for EO Exploitation Platforms, based on open standards. Supporting that, we are developing a reference implementation of building blocks, as free open source software.

The goal of the EOEPCA+ “Common Architecture” is therefore to define and agree the technical interfaces for the future exploitation of Earth Observation data in a distributed environment. The Common Architecture will provide the interfaces to facilitate the federation of different EO resources into a “Network of EO Resources”. The “Common Architecture” will be defined using open interfaces that link the different Resource Servers (building blocks) so that a user can efficiently access and consume the disparate services of the “Network of EO Resources”.

---

## EOEPCA+ Building Blocks

> **Bugs and Feature Requests**<br>
> Please report any [bugs](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) encountered, and we welcome [feature requests](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml).<br>
> These are triaged via our [`eoepca-plus`](https://github.com/EOEPCA/eoepca-plus) umbrella repository.

**User-defined Processing...**

| Building Block | Description |   |   |   |   |   |
|----------------|-------------|:-:|:-:|:-:|:-:|:-:|
| _Processing_<br>**OGC API Processes** | Execution of OGC Application Packages via OGC API Processes | [Docs](https://eoepca.readthedocs.io/projects/processing/en/latest/design/processing-engine/oa/) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/oapip-engine/) | [Repo](https://github.com/ZOO-Project/ZOO-Project) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| _Processing_<br>**openEO** | Programmtic execution of analytic workflows via openEO backends | [Docs](https://eoepca.readthedocs.io/projects/processing/en/latest/design/processing-engine/openeo/) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/openeo-engine/) | [Repo](https://github.com/Open-EO) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |

---

**Platform Resources...**

| Building Block | Description |   |   |   |   |   |
|----------------|-------------|:-:|:-:|:-:|:-:|:-:|
| **Resource Discovery** | Catalogue for platform resources | [Docs](https://eoepca.readthedocs.io/projects/resource-discovery) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-discovery/) | [Repo](https://github.com/EOEPCA/resource-discovery) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Resource Registration** | Ingesting resources into catalogue and access services | [Docs](https://eoepca.readthedocs.io/projects/resource-registration) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-registration/) | [Repo](https://github.com/EOEPCA/resource-registration) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Data Access** | Services for data retrieval and visualisation | [Docs](https://eoepca.readthedocs.io/projects/data-access) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/data-access/) | [Repo](https://github.com/EOEPCA/data-access) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Datacube Access** | Discovery, access and transformation of multi-dimensional data | [Docs](https://eoepca.readthedocs.io/projects/datacube-access) | _Coming<br>soon_ | [Repo](https://github.com/EOEPCA/datacube-access) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Workspace** | User/Project management of owned platform resources and services | [Docs](https://eoepca.readthedocs.io/projects/workspace) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/workspace/) | [Repo](https://github.com/EOEPCA/workspace) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |

---

**User Analysis and Exploitation...**

| Building Block | Description |   |   |   |   |   |
|----------------|-------------|:-:|:-:|:-:|:-:|:-:|
| **MLOps** | Machine Learning model development, training and asset management | [Docs](https://eoepca.readthedocs.io/projects/mlops) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/mlops/) | [Repo](https://github.com/csgroup-oss/sharinghub) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Application Hub** | Web-enabled interactive applications, dashboards and development tooling | [Docs](https://eoepca.readthedocs.io/projects/application-hub) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/application-hub/) | [Repo](https://github.com/EOEPCA/application-hub-context) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Application Quality** | Support best practice development for open science | [Docs](https://eoepca.readthedocs.io/projects/application-quality) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/application-quality/) | [Repo](https://github.com/EOEPCA/application-quality) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Resource Health** | Supports platform operators and users to monitor the health of their published resources | [Docs](https://eoepca.readthedocs.io/projects/resource-health) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-health/) | [Repo](https://github.com/EOEPCA/resource-health) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Notification & Automation** | Event-driven asynchronous communications with support for triggers linked to automated behaviour | [Docs](https://eoepca.readthedocs.io/technical/notification-automation-bb/) | _Coming<br>soon_ | [Repo](https://github.com/EOEPCA/document-notification-automation) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |

---

**Platform Federation...**

| Building Block | Description |   |   |   |   |   |
|----------------|-------------|:-:|:-:|:-:|:-:|:-:|
| **IAM** | Identity & Access Management | [Docs](https://eoepca.readthedocs.io/projects/iam) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/iam/main-iam/) | [Repo](https://github.com/EOEPCA/iam) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Federated Orchestrator** | Federation of workflow execution across multiple platforms | [Docs](https://eoepca.readthedocs.io/technical/federated-orchestrator-bb/) | _Coming<br>soon_ | [Repo](https://github.com/EOEPCA/document-federated-orchestrator) | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |
| **Data Gateway** | _Coming soon_<br>Consolidated discovery/access to the data offering of an extensible set of data providers | [Docs](https://eoepca.readthedocs.io/projects/architecture/en/latest/reference-architecture/data-gateway-BB/) | _Coming<br>soon_ | _Coming<br>soon_ | [Bug<br>Report](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) | [Feature<br>Request](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml) |

---

## Application Hub Applications

| Application | |
|-------------|-|
| **Processor Development Environment** | [Repo](https://github.com/EOEPCA/pde-code-server) |
| **JupyterLab** | [Repo](https://github.com/EOEPCA/iat-jupyterlab) |
| **Remote Desktop** | [Repo](https://github.com/EOEPCA/iga-remote-desktop) |
| **Remote Desktop with QGIS** | [Repo](https://github.com/EOEPCA/iga-remote-desktop-qgis) |
| **Remote Desktop with SNAP** | [Repo](https://github.com/EOEPCA/iga-remote-desktop-snap) |
| **Dashboard with Streamlit** | [Repo](https://github.com/EOEPCA/iga-streamlit-demo) |

## STAC Tools and Utilities

A collection of tools and utilities provided by EOEPCA and its partners that support use of STAC - in particular helpers for passing data in/out of processing workflows.

For more details see the [STAC Tools and Utilities](https://eoepca.readthedocs.io/technical/stac-tools-and-utilities/) page in the [EOEPCA+ Documentation](https://eoepca.readthedocs.io/).

| Tool | Description | |
|------|-------------|-|
| **STAC Catalogue Utilities** | Python library that helps to generate a STAC catalog from the files output as results of processing tasks. Motivated to support applications development in accordance with the OGC Best Practice for Application Packages | [Repo](https://github.com/EOEPCA/stac-cat-utils) |
| **MLOps STAC Abstractions** | Provides pre/post containers that are designed to be introduced into ML inference workflows to abstract the use of STAC in accordance with the OGC Best Practice for Application Packages | Repo<br>soon... |
| **STAC Catalogue Builder** | Tool that generates a STAC collection from a set of GeoTiff images - mainly intended to create STAC collections and catalogs for use in openEO, with the `load_stac` process | [Repo](https://github.com/VitoTAP/stac-catalog-builder) |
| **rio-stac** | Simple rasterio plugin (built on `pystac`) for creating valid STAC items from a raster dataset | [Repo](https://developmentseed.org/rio-stac/) |

See also [`stac-utils`](https://github.com/stac-utils).
