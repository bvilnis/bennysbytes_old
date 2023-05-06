---
title: "Conclusion and Next Steps"
description: "A summary of the project, highlighting its key features and benefits, and suggestions for further exploration and expansion."
tags: ["docs", "o11y-cluster"]
weight: 9
draft: false
---

In this wiki guide, we walked you through the process of deploying a local Kubernetes cluster using k3d, installing Helm, setting up a Helm repository, and deploying the Grafana Stack components (Prometheus, Loki, Tempo, and Grafana) using Helm charts. We also demonstrated how to expose Grafana using the NGINX Ingress Controller, access and configure Grafana dashboards, and perform troubleshooting and maintenance tasks.

With a fully functioning Grafana Stack deployment on your local Kubernetes cluster, you now have a powerful monitoring, logging, and tracing solution at your disposal. As next steps, consider the following:

1. **Deploy The New Stack (TNS) observability app:** In the upcoming part of this project, we will guide you through deploying [The New Stack (TNS) observability app](https://github.com/grafana/tns) by Grafana. This three-tier demo application is fully instrumented with the three pillars of observability: metrics, logs, and traces. By deploying TNS, you will gain insight into what a modern observability stack looks like and experience what it's like to pivot among different types of observability data.

2. **Customise your Grafana Stack:** Tailor your Grafana Stack deployment to your specific needs by customising the configuration options for each component. Consult the official Helm chart documentation for Prometheus, Loki, Tempo, and Grafana to explore the available configuration options.

3. **Explore advanced Grafana features:** Grafana offers a rich set of features that enable you to create advanced visualisations, set up alerting, and integrate with other tools and services. Dive deeper into the [Grafana documentation](https://grafana.com/docs/grafana/latest/) to learn more about these features.

4. **Monitor additional applications and services:** Expand your monitoring environment by adding additional applications and services to your Kubernetes cluster and configuring the appropriate data sources and dashboards in Grafana. You can find a wealth of pre-built dashboards and plugins on the [Grafana Dashboards](https://grafana.com/grafana/dashboards) and [Grafana Plugins](https://grafana.com/grafana/plugins) websites.

5. **Secure your Grafana Stack:** Ensure your monitoring environment is secure by implementing access controls, encryption, and other security best practices for each component of the Grafana Stack. Refer to the official documentation for each component to learn more about securing your deployment.

6. **Deploy the Grafana Stack on a production Kubernetes cluster:** Once you are comfortable with the Grafana Stack and have tailored it to your needs, consider deploying it on a production Kubernetes cluster to monitor your live applications and services.

By following this guide and exploring the suggested next steps, you are well-equipped to create a robust, scalable, and feature-rich monitoring environment for your applications and services using the Grafana Stack on Kubernetes. Stay tuned for the upcoming part of this project, where we will dive into deploying The New Stack (TNS) observability app and further enhance your monitoring experience.
