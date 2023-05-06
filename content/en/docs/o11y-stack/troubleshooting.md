---
title: "Troubleshooting and Maintenance"
description: "Tips and guidance for identifying and resolving common issues with the local Kubernetes cluster and Grafana Stack deployment, as well as best practices for maintaining and updating the cluster and its components."
tags: ["docs", "o11y-cluster"]
weight: 8
draft: false
---

In this section, we provide some general guidance on troubleshooting and maintaining your Grafana Stack deployment on your local Kubernetes cluster. These tips can help you identify and resolve common issues and ensure your monitoring environment remains healthy and up-to-date.

## Monitoring Cluster Resources
Keep an eye on your cluster resources (CPU, memory, and storage) to ensure your applications and services are running optimally. You can use Grafana itself to create dashboards that visualise resource usage for your Kubernetes cluster.

## Checking Logs
When experiencing issues with any component of the Grafana Stack, check the logs for errors or unexpected behavior. You can view the logs for a specific pod using the following command:

```bash
kubectl logs -n <namespace> <pod_name>
```

Replace `<namespace>` with the appropriate namespace (e.g., `prometheus`, `loki`, `tempo`, or `grafana`) and `<pod_name>` with the name of the pod you want to view the logs for.

## Upgrading Components
Keep the components of your Grafana Stack up-to-date by periodically upgrading the Helm charts. To upgrade a specific component, run the following command:

```bash
helm upgrade <release_name> grafana/<chart_name> --namespace <namespace>
```

Replace `<release_name>` with the name of the Helm release (e.g., `prometheus`, `loki`, `tempo`, or `grafana`), `<chart_name>` with the name of the Helm chart (e.g., `prometheus`, `loki`, `tempo`, or `grafana`), and `<namespace>` with the appropriate namespace.

Before upgrading, it is recommended to back up your configuration and data to ensure you can restore your environment if needed.

## Restarting Pods
If a component is not functioning correctly, you can try restarting the associated pod. To delete a specific pod and let Kubernetes automatically recreate it, run the following command:

```bash
kubectl delete pod -n <namespace> <pod_name>
```

Replace `<namespace>` with the appropriate namespace and `<pod_name>` with the name of the pod you want to delete.

## Scaling Cluster Resources
As your monitoring needs grow, you may need to scale your Grafana Stack components to handle increased load. You can scale your deployments by modifying the `replicaCount` value in the Helm chart values or by using the `kubectl scale` command:

```bash
kubectl scale deployment -n <namespace> <deployment_name> --replicas=<num_replicas>
```

Replace `<namespace>` with the appropriate namespace, `<deployment_name>` with the name of the deployment you want to scale, and `<num_replicas>` with the desired number of replicas.
