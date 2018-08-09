<p align="center">
<img src="https://raw.githubusercontent.com/kyma-project/kyma/master/logo.png" width="235">
</p>

## Overview

Kyma is a cloud-native application development framework.

It provides the last mile capabilities that a developer needs to build a cloud-native application using several open-source projects under the Cloud Native Computing Foundation (CNCF), such as Kubernetes, Istio, NATS, Kubeless, and Prometheus, to name a few.
It is designed natively on Kubernetes and, therefore, it is portable to all major cloud providers.

Kyma allows you to connect and extend products in a quick and modern way, using serverless computing and microservice architecture.

The extensions and customizations you create are decoupled from the core applications, which means that:
* deployments are quick
* scaling is independent from the core applications
* the changes you make can be easily reverted without causing downtime of the production system

Living outside of the core product, Kyma allows you to be completely language-agnostic and customize your solution using the technology stack you want to use, not the one the core product dictates. Additionally, Kyma follows the "batteries included" principle and comes with all of the "plumbing code" ready to use, allowing you to focus entirely on writing the domain code and business logic.

Read the [documentation](docs/README.md) to learn about the product, its technology stack, and components.

### Project structure

The repository has the following structure:

```
  ├── .github                     # Pull request and issue templates             
  ├── components                  # Source code of all Kyma components                                                   
  ├── docs                        # Documentation source files
  ├── installation                # Installation scripts     
  ├── resources                   # Helm charts and Kubernetes resources for the Kyma installation
  ├── tests                       # Acceptance tests
  └── tools                       # Source code of utilities used, for example, for the installation and testing
  ```

## Installation

Install Kyma [locally](docs/kyma/docs/031-gs-local-installation.md) and on a [cluster](docs/kyma/docs/032-gs-cluster-installation.md).

## Usage

Kyma comes with the ready-to-use code snippets that you can use to test the extensions and the core functionality. See the list of existing examples in the [`examples`](https://github.com/kyma-project/examples) repository.

## Development

Develop on your remote repository forked from the original repository in Go.
See the example that uses the [`ui-api-layer`](components/ui-api-layer) project located in the `components` directory in the `kyma` repository but applies to any Go project. This set of instructions uses the recommended [`git workflow`](https://github.com/kyma-project/community/blob/master/git-workflow.md) and the Kyma [contribution flow](https://github.com/kyma-project/community/blob/master/CONTRIBUTING.md#contribute-code-or-content).

Follow these steps:

> **NOTE:** The example assumes you have the `$GOPATH` already set.

1. Fork the repository in GitHub.

2. Clone the fork to your `$GOPATH` workspace. Use this command to create the folder structure and clone the repository under the correct location:

```
git clone git@github.com:{GitHubUsername}/kyma.git $GOPATH/src/github.com/kyma-project/kyma
```

Follow the steps described in the [`git-workflow.md`](https://github.com/kyma-project/community/blob/master/git-workflow.md#steps) document to configure your fork.

3. Install dependencies.

Go to the main directory of the project in your workspace location and install the required dependencies:

```
$ cd components/ui-api-layer
$ dep ensure -vendor-only
```

4. Build the project.

Every project runs differently. Follow instructions in the main `README.md` document of the given project to build it.

5. Create a branch and start to develop.

6. Test your changes.

When you finish, run unit and acceptance tests to verify your changes. For the unit tests, follow the instructions specified in the main `README.md` document of the given project. To run the acceptance tests, go to the `tests` directory for details.

7. Update the relevant documentation.

> **NOTE:** Successful unit and acceptance tests, and the documentation update are required to open a pull request.

7. Submit a pull request with your changes in code and wait for the owners' review and approval.
8. When you receive the required approvals, create another pull request to update the image version and any configuration changes in relevant Kyma charts.
