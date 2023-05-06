---
title: "Installing Helm and Setting Up Helm Repositories"
linkTitle: "Setting Up Helm"
description: "Instructions for installing Helm, configuring repositories, and an introduction to Helm charts and their usage in Kubernetes deployments."
tags: ["docs", "o11y-cluster"]
weight: 5
draft: false
---

In this section, I will guide you through the process of installing Helm and setting up a Helm repository on your macOS or Linux system. Helm is a package manager for Kubernetes that simplifies the deployment and management of applications and services on your cluster.

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
After installing Helm, you need to add the required Helm repositories for the Prometheus community chart, Grafana charts, and the Nginx ingress controller chart. Run the following commands to add the repositories:

1. Add the Prometheus community Helm repository:

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

2. Add the Grafana Helm repository:

```bash
helm repo add grafana https://grafana.github.io/helm-charts
```

3. Add the Nginx ingress controller Helm repository:

```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
```

Once the repository has been added, update your Helm repositories to fetch the latest charts:

```bash
helm repo update
```

This command synchronizes your local Helm repository index with the latest charts from the added repositories.

With Helm installed and the required repositories set up, you can now proceed with deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) and the Nginx ingress controller using Helm charts.
