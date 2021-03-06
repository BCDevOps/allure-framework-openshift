---
title: Allure Framework OpenShift
description: Get started with docs and resources for Allure Framework, a flexible lightweight multi-language test report tool.
author: esune
resourceType: Components
personas:
  - Developer
  - Product Owner
  - Designer
labels:
  - Allure Framework
  - Testing
  - Reporting
---

# Allure Framework OpenShift

Allure is a flexible, lightweight multi-language test report tool.

[Allure Framework OpenShift](https://github.com/BCDevOps/allure-framework-openshift) provides a set of OpenShift configurations to set up an instance of the Allure service and Allure UI. See: [docs.qameta.io/allure](https://docs.qameta.io/allure/) for additional details regarding Allure Framework.

The configurations in this repository are based on the [Allure Docker Service](https://github.com/fescobar/allure-docker-service) Docker images by [Frank Escobar](https://github.com/fescobar).

## Architecture

The service is composed by the following components:

- _allure_: the Allure server where the test results will be sent to be stored and aggregated for visualization.
- _allure-ui_: a frontend that allows the visualization of test reports.

## Deployment / Configuration

The templates provided in the `openshift` folder include everything that is necessary to create the required builds and deployments.

Since there are interdependencies between deployment configurations, please make sure to follow this order when creating them for the first time:

1. build and deploy the Allure service
2. build and deploy the Allure UI service

The [manage](./openshift/manage) script makes the process of adding a Allure instance to your project very easy. The script was build on the [openshift-developer-tools](https://github.com/BCDevOps/openshift-developer-tools) scripts.

Once you've cloned the repository, open a bash shell (Git Bash for example) to the `openshift` directory of the working copy.

The following example assumes an OpenShift project set named **ggpixq** ...

1. `./manage -n ggpixq init` - to initialize the configurations to be deployed into your project.
1. `./manage build` - to publish the build configuration(s) into your `tools` project and start the build.
1. `./manage -e prod deploy` - to publish the deployment configuration(s) into your `prod` environment and tag the application images to start the deployments.
1. Browse to the deployed application to complete the configuration.

_The deployment will have created a set of secrets for you to reference while completing the initial configuration: **allure-admin**, containing randomly generated credentials for your main super-user account._

For full script documentation run `./manage -h`.

_**Note:**_ some mandatory parameters are left blank in the template as they will be different for each deployment. Make sure you set values for all of them in the parameter files BEFORE generating the deployments in order to avoid issues.
In particular, it is important to set the `ALLURE_DOCKER_PUBLIC_API_URL` parameter in the `allure-ui` deployment to the URL that exposes the `allure` service.

## First Run

Once everything is up and running in OpenShift, please refer to the [Allure Docker service instructions](https://github.com/fescobar/allure-docker-service#table-of-contents) and the official [Allure Framework docs](https://docs.qameta.io/allure/) to set-up your reports.
