---
title: "Conclusion and Next Steps"
description: "A summary of the project, highlighting its key features and benefits, and suggestions for further exploration and expansion."
tags: ["docs", "o11y-cluster"]
weight: 8
draft: false
---

Congratulations! You have successfully set up a local Kubernetes cluster with k3d and deployed the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) and the Nginx ingress controller using Helm charts. With this foundation in place, you can now monitor your Kubernetes cluster's performance and health, and explore your cluster's metrics, logs, and traces using Grafana dashboards.

With a fully functioning Grafana Stack deployment on your local Kubernetes cluster, you now have a powerful monitoring, logging, and tracing solution at your disposal. As next steps, consider the following:

1. **Deploy The New Stack (TNS) observability app:** In the upcoming part of this project, I will guide you through deploying [The New Stack (TNS) observability app](https://github.com/grafana/tns) by Grafana. This three-tier demo application is fully instrumented with the three pillars of observability: metrics, logs, and traces. By deploying TNS, you will gain insight into what a modern observability stack looks like and experience what it's like to pivot among different types of observability data.

2. **Grafana Mimir:** I will also be including [Grafana Mimir](https://grafana.com/oss/mimir/) in the future update of this project. Mimir is a long-term metrics storage solution that provides a scalable, cost-effective, and easy-to-operate storage backend for Prometheus metrics. Integrating Mimir into your project will enable you to store and analyze historical metrics data, helping you identify trends and patterns over time.

3. **Customise your Grafana Stack:** Tailor your Grafana Stack deployment to your specific needs by customising the configuration options for each component. Consult the official Helm chart documentation for Prometheus, Loki, Tempo, and Grafana to explore the available configuration options.

4. **Explore advanced Grafana features:** Grafana offers a rich set of features that enable you to create advanced visualisations, set up alerting, and integrate with other tools and services. Dive deeper into the [Grafana documentation](https://grafana.com/docs/grafana/latest/) to learn more about these features.

5. **Monitor additional applications and services:** Expand your monitoring environment by adding additional applications and services to your Kubernetes cluster and configuring the appropriate data sources and dashboards in Grafana. You can find a wealth of pre-built dashboards and plugins on the [Grafana Dashboards](https://grafana.com/grafana/dashboards) and [Grafana Plugins](https://grafana.com/grafana/plugins) websites.

6. **Secure your Grafana Stack:** Ensure your monitoring environment is secure by implementing access controls, encryption, and other security best practices for each component of the Grafana Stack. Refer to the official documentation for each component to learn more about securing your deployment.

By following this guide and exploring the suggested next steps, you are well-equipped to create a robust, scalable, and feature-rich monitoring environment for your applications and services using the Grafana Stack on Kubernetes. Stay tuned for the upcoming part of this project, where I will dive into deploying The New Stack (TNS) observability app and Grafana Mimir to further enhance your observability experience.
