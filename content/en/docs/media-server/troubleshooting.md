---
title: "Troubleshooting and Maintenance"
description: "Common issues, solutions, and maintenance tasks for the Synology NAS media server setup."
tags: ["docs", "media-server"]
weight: 9
draft: false
---

## Troubleshooting and Maintenance

In this section, we'll provide some guidance on troubleshooting common issues and performing regular maintenance tasks for your media server.

### Troubleshooting Common Issues

1. **Container not starting or failing**: Check the container logs for any errors or issues by running `docker logs <container_name>`. This command will output the logs for the specified container, which can help you identify and resolve the issue.

2. **Networking issues**: If you're experiencing issues with containers that use the VPN container for network traffic, ensure that the VPN container is running and connected. Also, check the VPN container logs for any connection issues.

3. **Permission issues**: Make sure that the PUID and PGID environment variables are set correctly in your `docker-compose.yml` file. These variables should match the user and group IDs of the user running the Docker daemon on your Synology NAS.

### Regular Maintenance

1. **Backup your configuration and data**: Regularly backup the configuration files and data stored in the mounted volumes to prevent data loss in case of container failure or other issues.

2. **Monitor container resource usage**: Keep an eye on the resource usage of your containers, such as CPU, memory, and disk space. If a container is using excessive resources, consider optimizing its settings or upgrading your Synology NAS hardware if necessary.

3. **Keep your Synology NAS up-to-date**: Regularly update your Synology NAS's DSM operating system and installed packages to ensure optimal performance and security.

4. **Manually update containers**: If you have disabled the watchtower container or need to update a specific container to a non-latest version, you can manually pull the new image and recreate the container using the updated image. Remember to backup your configuration and data before performing manual updates.

By following these troubleshooting and maintenance guidelines, you can ensure a smooth and efficient operation of your media server setup on your Synology NAS.
