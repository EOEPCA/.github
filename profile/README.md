
# EOEPCA+ - EO Exploitation Platform Common Architecture

Architecture and software building-blocks for data exploitation and platform interoperability.

**EOEPCA+ Stable 2.0** is the current baseline release. 
See the [Release Notes](https://github.com/EOEPCA/deployment-guide/releases/tag/eoepca-2.0) and [2.0 Deployment Guide](https://eoepca.readthedocs.io/projects/deploy/en/eoepca-2.0/).

The previous EOEPCA release (v1.4) is still available via its [1.4 Deployment Guide](https://eoepca.readthedocs.io/projects/deploy/en/v1.4-stable/).

Migrating from an earlier version? See the [CHANGELOG](https://eoepca.readthedocs.io/projects/deploy/en/eoepca-2.0/changelog/) for more details.

---

## Overview

Earth Observation (EO) data has quickly evolved into an indispensable resource, directly facilitating solutions for society's most pressing challenges. This intensifying influx of data, oftentimes distributed across multiple independent platforms, presents a significant challenge for end-users in efficiently accessing and collaborating on critical geospatial tasks. Nevertheless, these platforms are more commonly collocated with cloud computing resources and applications such that users are now able to perform geospatial analysis tasks remotely. Working in the cloud bypasses traditional download, storage and performance limitations, however the distributed nature of these platform networks introduces complexities in the free and collective access to this remote geospatial data.

Our vision with EOEPCA+ then is for greater interoperability between such platforms, towards an open network of resources, whilst enabling current and future users to easily collaborate on geospatial analysis tasks at source. To this end we are helping to establish a consensus of best practice for EO Exploitation Platforms, based on open standards. Supporting that, we are developing a reference implementation of building blocks, as free open source software.

The goal of the EOEPCA+ "Common Architecture" is therefore to define and agree the technical interfaces for the future exploitation of Earth Observation data in a distributed environment. The Common Architecture will provide the interfaces to facilitate the federation of different EO resources into a "Network of EO Resources". The "Common Architecture" will be defined using open interfaces that link the different Resource Servers (building blocks) so that a user can efficiently access and consume the disparate services of the "Network of EO Resources".

---

## EOEPCA+ Building Blocks

> **Bugs and Feature Requests**<br>
> Please report any [bugs](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-bug.yaml) encountered, and we welcome [feature requests](https://github.com/EOEPCA/eoepca-plus/issues/new?template=eoepca-feature.yaml).<br>
> These are triaged via our [`eoepca-plus`](https://github.com/EOEPCA/eoepca-plus) umbrella repository.

> **Tutorials**<br>
> Building blocks have interactive tutorials that you can run in two ways. Some are available directly on [Killercoda](https://killercoda.com/eoepca). Most are provided as [Localcoda](https://github.com/spinto/localcoda) scenarios, which you run on your own machine or cluster. This is because many building blocks need more resources than Killercoda's VMs can provide. Clone the [scenario repo](https://github.com/EOEPCA/eoepca-killercoda), follow the Localcoda [README](https://github.com/spinto/localcoda#quickstart) to get it running, and point it at the scenario you want.

---

**Platform Resources...**

| Building Block | Status | Docs | Deploy | Repo | Notebook | Tutorial |
|----------------|:------:|:----:|:------:|:----:|:--------:|:--------:|
| **Data Access**<br>Services for data retrieval and visualisation | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/data-access) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/data-access/) | [Repo](https://github.com/EOEPCA/data-access) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/data-access/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/data-access) |
| **Resource Discovery**<br>Catalogue for platform resources | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/resource-discovery) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-discovery/) | [Repo](https://github.com/EOEPCA/resource-discovery) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/resource-discovery/) | [Killercoda](https://killercoda.com/eoepca/scenario/discovery) |
| **Resource Registration**<br>Ingesting resources into catalogue and access services | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/resource-registration) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-registration/) | [Repo](https://github.com/EOEPCA/resource-registration) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/resource-registration/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/registration) |
| **Datacube Access**<br>Discovery, access and transformation of multi-dimensional data | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/datacube-access) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/datacube-access/#collection-access-test) | [Repo](https://github.com/EOEPCA/datacube-access) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/datacube-access/) | [Killercoda](https://killercoda.com/eoepca/scenario/datacube-access) |
| **Workspace**<br>User/Project management of owned platform resources and services | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/workspace) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/workspace/) | [Repo](https://github.com/EOEPCA/workspace) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/workspace/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/workspace) |

---

**User-defined Processing...**

| Building Block | Status | Docs | Deploy | Repo | Notebook | Tutorial |
|----------------|:------:|:----:|:------:|:----:|:--------:|:--------:|
| **OGC API Processes** - _Processing_<br>Execution of OGC Application Packages via OGC API Processes | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/processing/en/latest/design/processing-engine/oa/) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/oapip-engine/) | [Repo](https://github.com/ZOO-Project/ZOO-Project) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/oapip/) | [Localcoda (Calrissian)](https://github.com/EOEPCA/eoepca-killercoda/tree/main/processing/calrissian)<br>[Killercoda (Toil)](https://killercoda.com/eoepca/course/processing/toil) |
| **openEO** - _Processing_<br>Programmatic execution of analytic workflows via openEO backends | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/processing/en/latest/design/processing-engine/openeo/) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/openeo-engine/) | [Repo](https://github.com/Open-EO) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/openeo/) | [Localcoda (Geotrellis)](https://github.com/EOEPCA/eoepca-killercoda/tree/main/processing/openeo-geotrellis) |

---

**User Analysis and Exploitation...**

| Building Block | Status | Docs | Deploy | Repo | Notebook | Tutorial |
|----------------|:------:|:----:|:------:|:----:|:--------:|:--------:|
| **Application Hub**<br>Web-enabled interactive applications, dashboards and development tooling | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/application-hub) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/application-hub/) | [Repo](https://github.com/EOEPCA/application-hub-context) | N/A | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/app-hub) |
| **Application Quality**<br>Support best practice development for open science | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/application-quality) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/application-quality/) | [Repo](https://github.com/EOEPCA/application-quality) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/application-quality/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/monitoring/application-quality) |
| **MLOps**<br>Machine Learning model development, training and asset management | Release Candidate | [Docs](https://eoepca.readthedocs.io/projects/mlops) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/mlops/) | [Repo](https://github.com/csgroup-oss/sharinghub) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/mlops/) | _Coming<br>soon_ |
| **Resource Health**<br>Supports platform operators and users to monitor the health of their published resources | Release Candidate | [Docs](https://eoepca.readthedocs.io/projects/resource-health) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/resource-health/) | [Repo](https://github.com/EOEPCA/resource-health) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/resource-health/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/monitoring/resource-health) |
| **Notification & Automation**<br>Event-driven asynchronous communications with support for triggers linked to automated behaviour | Coming Soon | [Docs](https://eoepca.readthedocs.io/technical/notification-automation-bb/) | _Coming<br>soon_ | [Repo](https://github.com/EOEPCA/document-notification-automation) | _Coming<br>soon_ | _Coming<br>soon_ |
---

**Platform Federation...**

| Building Block | Status | Docs | Deploy | Repo | Notebook | Tutorial |
|----------------|:------:|:----:|:------:|:----:|:--------:|:--------:|
| **IAM**<br>Identity & Access Management | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/iam) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/iam/main-iam/) | [Repo](https://github.com/EOEPCA/iam) | [Notebook](https://github.com/EOEPCA/deployment-guide/blob/main/notebooks/examples/iam/) | [Localcoda](https://github.com/EOEPCA/eoepca-killercoda/tree/main/iam) |
| **Data Gateway**<br>Consolidated discovery/access to the data offering of an extensible set of data providers | 2.0 Stable | [Docs](https://eoepca.readthedocs.io/projects/architecture/en/latest/reference-architecture/data-gateway-BB/) | [Deploy](https://eoepca.readthedocs.io/projects/deploy/en/latest/building-blocks/data-gateway/) | [Repo](https://github.com/CS-SI/eodag) | [Notebook](https://eodag.readthedocs.io/en/stable/tutos.html#tutos) | [Killercoda](https://killercoda.com/eoepca/scenario/data-gateway) |
| **Federated Orchestrator**<br>Federation of workflow execution across multiple platforms | Coming Soon | [Docs](https://eoepca.readthedocs.io/technical/federated-orchestrator-bb/) | _Coming<br>soon_ | [Repo](https://github.com/EOEPCA/document-federated-orchestrator) | _Coming<br>soon_ | _Coming<br>soon_ |
---

## Application Hub Applications

| Application | |
|-------------|-|
| **Processor Development Environment** | [Repo](https://github.com/EOEPCA/pde-code-server) |
| **JupyterLab** | [Repo](https://github.com/EOEPCA/iat-jupyterlab) |
| **Remote Desktop** | [Repo](https://github.com/EOEPCA/iga-remote-desktop) |
| **Remote Desktop with QGIS** | [Repo](https://github.com/EOEPCA/iga-remote-desktop-qgis) |
| **Remote Desktop with SNAP** | [Repo](https://github.com/EOEPCA/iga-remote-desktop-snap) |
| **Remote Desktop with Panoply** | [Repo](https://github.com/EOEPCA/iga-remote-desktop-panoply) |
| **Dashboard with Streamlit** | [Repo](https://github.com/EOEPCA/iga-streamlit-demo) |

## STAC Tools and Utilities

A collection of tools and utilities provided by EOEPCA and its partners that support use of STAC - in particular helpers for passing data in/out of processing workflows.

For more details see the [STAC Tools and Utilities](https://eoepca.readthedocs.io/technical/stac-tools-and-utilities/) page in the [EOEPCA+ Documentation](https://eoepca.readthedocs.io/).

| Tool | Description | |
|------|-------------|-|
| **EODAG** | Generic data gateway providing consolidated discovery and access across multiple data providers. Also offers the Python function `augment_with_xarray` for extracting metadata from data and generating STAC-compliant representations | [Repo](https://github.com/CS-SI/eodag) |
| **STAC Catalogue Utilities** | Python library that helps to generate a STAC catalog from the files output as results of processing tasks. Motivated to support applications development in accordance with the OGC Best Practice for Application Packages | [Repo](https://github.com/EOEPCA/stac-cat-utils) |
| **MLOps STAC Abstractions** | Provides pre/post containers that are designed to be introduced into ML inference workflows to abstract the use of STAC in accordance with the OGC Best Practice for Application Packages | Repo<br>soon... |
| **STAC Catalogue Builder** | Tool that generates a STAC collection from a set of GeoTiff images - mainly intended to create STAC collections and catalogs for use in openEO, with the `load_stac` process | [Repo](https://github.com/VitoTAP/stac-catalog-builder) |
| **rio-stac** | Simple rasterio plugin (built on `pystac`) for creating valid STAC items from a raster dataset | [Repo](https://developmentseed.org/rio-stac/) |

See also [`stac-utils`](https://github.com/stac-utils).



