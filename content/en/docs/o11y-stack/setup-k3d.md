---
title: "Installing and Setting Up a k3d cluster"
linkTitle: "Setting Up k3d"
description: "Detailed guidance on creating and managing a local Kubernetes cluster using k3d, with explanations of key concepts and commands."
tags: ["docs", "o11y-cluster"]
weight: 4
draft: false
---

In this section, we will guide you through the process of creating and managing a local Kubernetes cluster using k3d on macOS and Linux systems. The instructions provided below are applicable to both operating systems.

## macOS Installation
To install k3d on macOS, you can use the Homebrew package manager. If you don't have Homebrew installed, follow the instructions on the [Homebrew website](https://brew.sh/) to install it. Once Homebrew is installed, run the following command in your terminal to install k3d:

```bash
brew install k3d
```
After the installation is complete, verify that k3d is correctly installed by running:

```bash
k3d version
```

## Linux Installation
To install k3d on Linux, you can use the following installation script provided by the k3d project. Open your terminal and run the following command:

```bash
curl -s https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash
```

This command downloads and runs the installation script, which installs k3d on your Linux system. After the installation is complete, verify that k3d is correctly installed by running:

```bash
k3d version
```

## Alternative Installation Method
Alternatively, you can download the latest k3d binary from the [k3d GitHub releases page](https://github.com/rancher/k3d/releases) and place it in a directory listed in your system's PATH environment variable. Make sure to give the binary executable permissions:

```bash
chmod +x /path/to/k3d
```

Replace `/path/to/k3d` with the actual path to the downloaded k3d binary.

Now that k3d is installed on your macOS or Linux system, you can proceed with setting up a local Kubernetes cluster using k3d.

## Creating a Kubernetes Cluster
To create a local Kubernetes cluster with k3d, use the following command:

```bash
k3d cluster create my-cluster
```

Replace `my-cluster` with the desired name for your Kubernetes cluster. This command creates a single-node cluster (one server node) with a default configuration. k3d automatically sets up the Kubernetes API, kubelet, and other essential components within the cluster.

After the cluster has been created, k3d configures your `kubectl` to point to the new cluster by updating your kubeconfig file. You can verify that `kubectl` is correctly configured by running:

```bash
kubectl cluster-info
```

## Customising the Cluster Configuration
k3d allows you to customise your Kubernetes cluster by specifying additional options when creating the cluster. For example, to create a multi-node cluster with three server nodes and two agent nodes, you can use the following command:

```bash
k3d cluster create my-cluster --servers 3 --agents 2
```

Replace my-cluster with the desired name for your Kubernetes cluster. This command creates a Kubernetes cluster with a total of five nodes: three server nodes that run the Kubernetes control plane components and two agent nodes that run your workloads.

For more advanced configuration options, refer to the [k3d documentation](https://k3d.io/).

## Deleting the Kubernetes Cluster
To delete a local Kubernetes cluster created with k3d, use the following command:

```bash
k3d cluster delete my-cluster
```

Replace `my-cluster` with the name of the Kubernetes cluster you want to delete. This command removes all resources associated with the specified cluster.

With your local Kubernetes cluster set up using k3d, you can now proceed with installing Helm and deploying the Grafana Stack using Helm charts.
