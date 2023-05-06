---
title: "Accessing and Configuring Grafana Dashboards"
linkTitle: "Access and Setup Grafana"
description: "Instructions for accessing the Grafana dashboard, connecting data sources, and configuring visualisations for monitoring, logging, and tracing."
tags: ["docs", "o11y-cluster"]
weight: 7
draft: false
---

In this section, we will guide you through the process of exposing Grafana using the NGINX Ingress Controller and accessing its dashboards to visualise the data from Prometheus, Loki, and Tempo.

## Installing NGINX Ingress Controller
The NGINX Ingress Controller is a Kubernetes Ingress implementation that uses NGINX as a reverse proxy and load balancer. We will use the NGINX Ingress Controller Helm chart to expose Grafana.

1. Create a namespace for the NGINX Ingress Controller:

```bash
kubectl create namespace ingress-nginx
```

2. Install the NGINX Ingress Controller Helm chart:

```bash
helm install ingress-nginx ingress-nginx/ingress-nginx --namespace ingress-nginx
```

This command installs the NGINX Ingress Controller in the `ingress-nginx` namespace using the default configuration provided by the ingress-nginx Helm repository.

3. Verify that the NGINX Ingress Controller is running:

```bash
kubectl get pods --namespace ingress-nginx
```

This command should display the running NGINX Ingress Controller pods in the `ingress-nginx` namespace.

## Exposing Grafana using the NGINX Ingress Controller
Now that the NGINX Ingress Controller is installed, we will create an Ingress resource to expose Grafana.

1. Create a `grafana-ingress.yaml` file with the following contents:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: grafana
  namespace: grafana
  annotations:
    kubernetes.io/ingress.class: "nginx"
spec:
  rules:
  - host: grafana.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: grafana
            port:
              number: 80
```

Replace `grafana.local` with the desired hostname for accessing Grafana. Ensure that the specified hostname resolves to your Kubernetes cluster's IP address or localhost by updating your `/etc/hosts` file.

2. Apply the Ingress resource:

```bash
kubectl apply -f grafana-ingress.yaml
```

This command creates an Ingress resource that routes traffic to the Grafana service in the `grafana` namespace.

## Accessing Grafana Dashboards
With Grafana exposed using the NGINX Ingress Controller, you can now access its user interface to configure data sources and dashboards.

1. Open your web browser and navigate to the Grafana hostname specified in the Ingress resource (e.g., `http://grafana.local`).

2. Log in to Grafana using the default credentials:

    - Username: `admin`
    - Password: `admin`

3. After logging in, you will be prompted to change the default password. Set a new password for the `admin` user.

4. Add data sources for Prometheus, Loki, and Tempo:

    - Click on the gear icon in the left sidebar to open the configuration menu.
    - Click on "Data sources" and then "Add data source."
    - For each data source, select its type (Prometheus, Loki, or Tempo) and provide the necessary information, such as the service URL and authentication details.

5. Import or create Grafana dashboards to visualise the data from Prometheus, Loki, and Tempo:
    - Click on the "+" icon in the left sidebar to open the "Create" menu.
    - Click on "Import" to import pre-built dashboards using their dashboard IDs or JSON files. You can find a variety of pre-built dashboards for Prometheus, Loki, and Tempo on the [Grafana Dashboards](https://grafana.com/grafana/dashboards) website.
    - Alternatively, click on "Dashboard" to create a new, custom dashboard. Add panels to the dashboard and configure them to display the desired metrics, logs, or traces from your data sources. For more information on creating custom dashboards, refer to the [Grafana documentation](https://grafana.com/docs/grafana/latest/dashboards/).

With your Grafana dashboards set up, you can now monitor, explore, and analyze the data from Prometheus, Loki, and Tempo in a single, unified interface.

You have successfully deployed the Grafana Stack using Helm charts on your local Kubernetes cluster and exposed Grafana using the NGINX Ingress Controller. This powerful combination enables you to easily manage and visualise your applications' performance and health.
