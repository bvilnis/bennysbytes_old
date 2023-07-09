---
title: "Troubleshooting and Maintenance"
description: "Common issues, solutions, and maintenance tasks for the Synology NAS media server setup."
tags: ["docs", "media-server"]
weight: 6
draft: false
---

## Troubleshooting and Maintenance

This section will guide you through resolving common issues that may arise during the operation of your media server, as well as regular maintenance to keep things running smoothly.

### Troubleshooting Common Issues

#### Applications Not Starting

If you find an application isn't starting, check its logs in the "Log Center" on your Synology NAS. The error messages provided should help you identify and fix the issue.

#### Connection Issues

When you encounter connection problems between applications, it could be due to network configuration issues. Ensure your Synology NAS is correctly configured to allow the required connections, and that your network router is not blocking any required ports.

#### Access Permission Issues

Access permissions are often the cause of various issues. Be sure that all the necessary permissions are set correctly in your DSM. For example, the user group assigned to the apps should have read/write access to the directories they need.

### Regular Maintenance

#### Backup Configuration and Data

To avoid data loss, regularly back up your Synology NAS data, including application configurations and media files. You can utilize Synology's built-in Hyper Backup utility for this task.

#### Monitor Resource Usage

Keep an eye on your Synology NAS's resource usage. If it is frequently running low on CPU, RAM, or storage space, you might need to optimize your setup or consider a hardware upgrade.

#### Update Your Synology NAS and Packages

Ensure your DSM operating system and all installed packages are up-to-date to benefit from the latest features and security patches. Regular updates will help maintain the optimal performance and security of your media server.

#### Update Applications When Necessary

While the applications installed from the SynoCommunity should automatically update, occasionally you may need to manually update an application to get the latest features or bug fixes. Always ensure to back up your configurations before performing updates.

Adhering to these troubleshooting and maintenance tips can help to maintain a stable and efficient operation of your media server setup on your Synology NAS.
