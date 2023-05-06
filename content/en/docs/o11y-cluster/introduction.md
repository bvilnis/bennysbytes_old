---
title: "Introduction"
description: "A brief introduction to Kubernetes, k3d, Grafana Stack, and Helm charts, explaining their importance and relevance to the project."
tags: ["docs", "o11y-cluster"]
weight: 1
draft: false
---

Welcome to this comprehensive guide on setting up a local Kubernetes cluster using k3d and deploying the Grafana Stack (Prometheus, Loki, Tempo, and Grafana) using Helm charts on macOS and Linux systems. In this introduction, I will briefly explain the key technologies involved in this project and their relevance.

## Kubernetes
[Kubernetes](https://kubernetes.io/) is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerised applications. It provides a powerful and flexible framework for managing containerised workloads and services, enabling efficient use of resources, high availability, and seamless updates.

## k3d
[k3d](https://k3d.io/) is a lightweight tool that allows you to run k3s, a highly available, certified Kubernetes distribution designed for low-resource environments, inside Docker containers. k3d simplifies the process of setting up a local Kubernetes cluster on your development machine, making it an ideal choice for developers who want to test and experiment with Kubernetes without the overhead of a full-scale cluster.

## Grafana Stack
The Grafana Stack is a collection of open-source monitoring, logging, and tracing tools designed to provide comprehensive observability for your applications and infrastructure. The stack includes:

- **[Prometheus](https://prometheus.io/):** A powerful time-series database and monitoring system that collects and stores metrics from various sources, providing real-time insights into the performance and health of your applications and infrastructure.
- **[Loki](https://grafana.com/logs/):** A horizontally-scalable, highly-available log aggregation system that collects and stores log data, making it easy to search, explore, and analyze logs from your applications and services.
- **[Tempo](https://grafana.com/traces/):** A distributed tracing system that collects, processes, and stores traces from your applications, providing in-depth visibility into the performance and behavior of distributed systems.
- **[Grafana](https://grafana.com/grafana/):** A versatile visualisation platform that brings together data from various sources, including Prometheus, Loki, and Tempo, allowing you to create customisable and interactive dashboards for monitoring, logging, and tracing.

## Helm Charts
[Helm](https://helm.sh/) is a package manager for Kubernetes that simplifies the deployment and management of applications and services on your cluster. Helm uses a packaging format called charts, which are collections of files describing a related set of Kubernetes resources. Helm charts allow you to define, version, share, and deploy complex applications and services with ease, making them an ideal choice for deploying the Grafana Stack on your local Kubernetes cluster.

By following this guide, you will learn how to set up a local Kubernetes cluster using k3d, install Helm, and deploy the Grafana Stack using Helm charts on macOS and Linux systems. This will enable you to monitor, log, and trace your applications and services, gaining valuable insights into their performance and behavior.
