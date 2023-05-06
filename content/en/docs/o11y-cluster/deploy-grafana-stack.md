---
title: "Deploying the Grafana Stack using Helm Charts"
linkTitle: "Deploying Grafana Stack"
description: "A comprehensive guide on deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) using Helm charts."
tags: ["docs", "o11y-cluster"]
weight: 6
draft: false
---

In this section, I will guide you through the process of deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) and the Nginx ingress controller on your local Kubernetes cluster using Helm charts.

## Deploying the kube-prometheus-stack Chart
The `kube-prometheus-stack` chart from the Prometheus community repository includes Prometheus, Alertmanager, and Grafana, as well as the necessary exporters and service monitors for Kubernetes cluster monitoring.

1. Create a namespace for the Grafana Stack components:

```bash
kubectl create namespace monitoring
```

2. Install the `kube-prometheus-stack` Helm chart:

```bash
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
```

This command deploys Prometheus, Alertmanager, Grafana, and related components in the `monitoring` namespace.

## Deploying Loki
To deploy Loki, use the `loki` chart from the Grafana repository.

1. Install the `loki` Helm chart:

```bash
helm install loki grafana/loki --namespace monitoring
```

This command deploys Loki in the `monitoring` namespace.

## Deploying Tempo
To deploy Tempo, use the `tempo` chart from the Grafana repository.

1. Install the `tempo` Helm chart:

```bash
helm install tempo grafana/tempo --namespace monitoring
```

This command deploys Tempo in the `monitoring` namespace.

## Deploying the Nginx Ingress Controller
The Nginx ingress controller is required to expose and access Grafana outside the Kubernetes cluster.

1. Create a namespace for the Nginx ingress controller:

```bash
kubectl create namespace ingress
```

2. Install the `ingress-nginx` Helm chart:

```bash
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace ingress
```

This command deploys the Nginx ingress controller in the ingress namespace.

## Accessing Grafana
To access Grafana, you need to create an ingress resource that maps a domain name to the Grafana service.

1. Create a file named `grafana-ingress.yaml` with the following content:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: grafana
  namespace: monitoring
  annotations:
    kubernetes.io/ingress.class: nginx
spec:
  rules:
  - host: grafana.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: prometheus-grafana
            port:
              number: 80
```

Replace `grafana.local` with the desired domain name for accessing Grafana.

2. Apply the ingress resource:

```bash
kubectl apply -f grafana-ingress.yaml
```

3. Update your `/etc/hosts` file to map the domain name to your local Kubernetes cluster's ingress IP address. Find the IP address by running:

```bash
kubectl get ingress -n monitoring grafana -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
```

Add the following line to your hosts file:

```lua
<IP_ADDRESS> grafana.local
```

Replace `<IP_ADDRESS>` with the actual IP address and `grafana.local` with the domain name you used in the `grafana-ingress.yaml` file.

4. Access Grafana by opening your web browser and navigating to the domain name specified in the ingress resource (e.g., `http://grafana.local`). The default username and password for Grafana are `admin`. On your first login, you will be prompted to change the password.

## Configuring Grafana Data Sources
After accessing Grafana, you need to configure the data sources for Prometheus, Loki, and Tempo.

1. Configure the Prometheus data source by navigating to `Configuration > Data Sources` in the Grafana side menu, clicking on `Add data source`, and selecting `Prometheus`. Set the URL to `http://prometheus-kube-prometheus-prometheus.monitoring:9090` and click on `Save & Test`.

2. Configure the Loki data source by navigating to `Configuration > Data Sources` in the Grafana side menu, clicking on `Add data source`, and selecting `Loki`. Set the URL to `http://loki.monitoring:3100` and click on `Save & Test`.

3. Configure the Tempo data source by navigating to `Configuration > Data Sources` in the Grafana side menu, clicking on `Add data source`, and selecting `Tempo`. Set the URL to `http://tempo.monitoring:3200` and click on `Save & Test`.

With the Grafana Stack components and the Nginx ingress controller deployed on your local Kubernetes cluster and Grafana configured with the appropriate data sources, you can now start exploring your cluster's metrics, logs, and traces using Grafana dashboards.
