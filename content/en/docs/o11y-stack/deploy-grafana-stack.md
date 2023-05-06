---
title: "Deploying the Grafana Stack using Helm Charts"
linkTitle: "Deploying Grafana Stack"
description: "A comprehensive guide on deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) using Helm charts, including detailed explanations of chart configurations and customisations."
tags: ["docs", "o11y-cluster"]
weight: 6
draft: false
---

In this section, we will guide you through the process of deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) using Helm charts on your local Kubernetes cluster. We will deploy each component separately, providing step-by-step instructions for each.

## Deploying Prometheus
Prometheus is a powerful time-series database and monitoring system that collects and stores metrics from various sources, providing real-time insights into the performance and health of your applications and infrastructure.

1. Create a namespace for Prometheus:

```bash
kubectl create namespace prometheus
```

2. Install the Prometheus Helm chart:

```bash
helm install prometheus prometheus-community/prometheus --namespace prometheus
```

This command installs Prometheus in the `prometheus` namespace using the default configuration provided by the Grafana Helm repository.

3. Verify that Prometheus is running:

```bash
kubectl get pods --namespace prometheus
```

This command should display the running Prometheus pods in the `prometheus` namespace.

## Deploying Loki
Loki is a horizontally-scalable, highly-available log aggregation system that collects and stores log data, making it easy to search, explore, and analyze logs from your applications and services.

1. Create a namespace for Loki:

```bash
kubectl create namespace loki
```

2. Install the Loki Helm chart:

```bash
helm install loki grafana/loki --namespace loki
```

This command installs Loki in the `loki` namespace using the default configuration provided by the Grafana Helm repository.

3. Verify that Loki is running:

```bash
kubectl get pods --namespace loki
```

This command should display the running Loki pods in the `loki` namespace.

## Deploying Tempo

Tempo is a distributed tracing system that collects, processes, and stores traces from your applications, providing in-depth visibility into the performance and behavior of distributed systems.

1. Create a namespace for Tempo:

```bash
kubectl create namespace tempo
```

2. Install the Tempo Helm chart:

```bash
helm install tempo grafana/tempo --namespace tempo
```

This command installs Tempo in the `tempo` namespace using the default configuration provided by the Grafana Helm repository.

3. Verify that Tempo is running:

```bash
kubectl get pods --namespace tempo
```

This command should display the running Tempo pods in the `tempo` namespace.

## Deploying Grafana
Grafana is a versatile visualization platform that brings together data from various sources, including Prometheus, Loki, and Tempo, allowing you to create customizable and interactive dashboards for monitoring, logging, and tracing.

1. Create a namespace for Grafana:

```bash
kubectl create namespace grafana
```

2. Install the Grafana Helm chart:

```bash
helm install grafana grafana/grafana --namespace grafana
```

This command installs Grafana in the `grafana` namespace using the default configuration provided by the Grafana Helm repository.

3. Verify that Grafana is running:

```bash
kubectl get pods --namespace grafana
```

This command should display the running Grafana pods in the `grafana` namespace.

With all Grafana Stack components deployed on your local Kubernetes cluster, you can now configure data sources and dashboards in Grafana to visualize the data from Prometheus, Loki, and Tempo.
