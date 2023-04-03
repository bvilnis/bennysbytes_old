---
title: "Automating Container Updates"
description: "Setting up Watchtower to automatically update containers and scheduling the task."
tags: ["docs", "media-server"]
weight: 8
draft: false
---

## Automating the Container Updates

In the provided `docker-compose.yml` file, a container named `watchtower` has been set up to automatically check for and update all other containers within the compose file to their latest available versions. The watchtower container has been configured to run on a schedule, checking for updates every Monday at 2 AM.

To provide a brief overview of how this works:

1. The watchtower container is configured with the `containrrr/watchtower` image.
2. It has access to the Docker daemon by mounting `/var/run/docker.sock`.
3. The `command` parameter is set to `--schedule "0 2 * * MON"`, which defines the schedule to check for updates (every Monday at 2 AM).

With this setup, you don't need to manually check for updates and restart your containers. Watchtower will handle this task automatically, ensuring that your media server is always up-to-date with the latest features and bug fixes.

However, if you want to disable automatic updates, you can simply comment out or remove the watchtower container from your `docker-compose.yml` file. To manually update a container, you'll need to pull the latest image and recreate the container using the updated image.

Keep in mind that watchtower updates containers without losing their configurations or data, as long as the containers have their configuration and data stored in mounted volumes outside the container (as configured in the `docker-compose.yml` file).

{{% pageinfo %}}
**Note**: In the event of an update causing issues with a container, you may need to rollback to a previous version of the container's image. It is recommended to regularly backup your configuration and data files to avoid data loss.
{{% /pageinfo %}}