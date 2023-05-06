---
title: "Installing Helm and Setting Up a Helm Repository"
linkTitle: "Setting Up Helm"
description: "Instructions for installing Helm, configuring repositories, and an introduction to Helm charts and their usage in Kubernetes deployments."
tags: ["docs", "o11y-cluster"]
weight: 5
draft: false
---

In this section, we will guide you through the process of installing Helm and setting up a Helm repository on your macOS or Linux system. Helm is a package manager for Kubernetes that simplifies the deployment and management of applications and services on your cluster.

## Installing Helm
To install Helm, follow the instructions provided in the [official Helm documentation](https://helm.sh/docs/intro/install/). The installation process varies depending on your operating system:

  - For macOS users, you can use the Homebrew package manager to install Helm:
  ```bash
  brew install helm
  ```

  - For Linux users, you can use the installation script provided by Helm:
  ```bash
  curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
  chmod 700 get_helm.sh
  /get_helm.sh
  ```

After the installation is complete, verify that Helm is correctly installed by running:

```bash
helm version
```

## Setting Up The Helm Repositories
Helm repositories are collections of Helm charts that can be easily accessed and installed on your Kubernetes cluster. To deploy the Grafana Stack and access it via an NGINX ingress controller, you will need to add the official Grafana and NGINX Helm repositories to your Helm configuration.

Add the Grafana and NGINX Helm repositories using the following command:

```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
```

Once the repository has been added, update your Helm repositories to fetch the latest charts:


```bash
helm repo update
```

With Helm installed and the Grafana Helm repository set up, you can now proceed with deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) using Helm charts on your local Kubernetes cluster.
