---
title: "Prerequisites"
description: "A list of prerequisites and system requirements for setting up a local Kubernetes cluster on a Mac Mini and deploying the Grafana Stack using Helm charts."
tags: ["docs", "o11y-cluster"]
weight: 2
draft: false
---

Before proceeding with setting up a local Kubernetes cluster using k3d and deploying the Grafana Stack using Helm charts, ensure that your macOS or Linux system meets the following prerequisites:

1. **Hardware Requirements:** Although k3d is designed for low-resource environments, it is recommended to have a system with at least 4 GB of RAM and a multi-core processor to run the Kubernetes cluster and the Grafana Stack smoothly.

2. **Operating Systems:** This guide supports macOS (10.14 Mojave or newer) and Linux systems (Debian, Ubuntu, Fedora, or CentOS). Ensure that your system is up-to-date and running a compatible version of the OS.

3. **Docker:** Docker is required to run k3d, as it creates and manages k3s clusters inside Docker containers. Install the latest version of Docker Desktop for macOS or Linux, following the [official documentation](https://docs.docker.com/desktop/).

4. **kubectl:** kubectl is the command-line tool for interacting with Kubernetes clusters. Install kubectl using the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

5. **Basic Command-Line and Terminal Knowledge:** Familiarity with the command-line interface (CLI) and terminal operations on macOS or Linux is essential for following the instructions in this guide.

Once you have ensured that your system meets the prerequisites, you can proceed with the installation of k3d and the setup of a local Kubernetes cluster, followed by the deployment of the Grafana Stack using Helm charts.
