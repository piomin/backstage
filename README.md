# Backstage with Plugins [![Twitter](https://img.shields.io/twitter/follow/piotr_minkowski.svg?style=social&logo=twitter&label=Follow%20Me)](https://twitter.com/piotr_minkowski)

In this project, I'm creating my instance of the [Backstage](https://backstage.io) app with the set of plugins.

## Introduction
This instance of Backstage contains the following plugins:
* CircleCI
* Sonarqube
* GitHub
* Kubernetes
* HTTP Request Action
* Argo CD
* Prometheus

## Installation

In order to start it locally, run:
```sh
yarn install
yarn dev
```

Before starting it, you generate and export tokens for CircleCI, GitHub, Sonarqube and Argo CD as environment variables:
```sh
export CIRCLECI_TOKEN=<YOUR_CIRCLECI_TOKEN>
export SONARCLOUD_TOKEN=<YOUR_SONARCLOUD_TOKEN>
export GITHUB_TOKEN=<YOUR_GITHUB_TOKEN>
export ARGOCD_TOKEN=<YOUR_ARGOCD_TOKEN>
```

## Run on Docker
You can use my image of Backstage built from that repo. Just use the following command:
```shell
docker run -it -p 7007:7007 \
  -e GITHUB_TOKEN=<YOUR_GITHUB_TOKEN> \
  -e SONARCLOUD_TOKEN=<YOUR_SONARCLOUD_TOKEN> \
  -e ARGOCD_TOKEN=<YOUR_ARGOCD_TOKEN> \
  -e CIRCLECI_TOKEN=<YOUR_CIRCLECI_TOKEN> \
  -e NODE_ENV=development \
  piomin/backstage:latest
```

## Customization

You can add and configure additional plugins to the Backstage instance. Once you do it, you can rebuild the project and create your own Docker image:
```shell
yarn install
yarn tsc
yarn build:backend
yarn build-image
```