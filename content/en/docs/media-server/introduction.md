---
title: "Introduction"
description: "Overview of the Synology NAS media server setup using Docker and Docker Compose."
tags: ["docs", "media-server"]
weight: 1
draft: false
---

## Introduction

This guide provides a comprehensive overview of setting up a media server on a Synology DS220+ NAS using Docker and Docker Compose. The Synology DS220+ is a powerful and versatile NAS device, suitable for various tasks such as file storage, media streaming, and running containerized applications. In this setup, we will be using two Seagate Ironwolf NAS 10TB hard drives for storage.

The media server setup will include popular applications like Sonarr, Radarr, Plex, and others, all running within Docker containers. Docker and Docker Compose will be used to simplify the deployment and management of these applications.

### Overview

By following this guide, you will learn how to:

- Set up the Synology DS220+ NAS for the first time.
- Enable SSH and install Docker and Docker Compose.
- Create the necessary directories for container configurations and media files.
- Configure the `docker-compose.yml` file with the desired media server applications.
- Create the `/dev/net/tun` device for the VPN container.
- Start and manage the media server containers using Docker Compose.
- Set up Watchtower to automate container updates.
- Perform basic troubleshooting and maintenance tasks.

Once completed, you will have a fully functional media server running on your Synology DS220+ NAS with easy-to-use applications for managing your media library, downloading new content, and streaming media to your devices.

### Components

#### Hardware

- [Synology DS220+ NAS](https://www.synology.com/en-us/products/DS220+)
- 2x [Seagate Ironwolf NAS 10TB hard drives](https://www.seagate.com/au/en/products/nas-drives/ironwolf-hard-drive/)

#### Software

- [Docker](https://docs.docker.com/get-started/overview/)
- [Docker Compose](https://docs.docker.com/compose/)

#### Applications

- [Sonarr](https://sonarr.tv/): TV show management and download automation.
- [Radarr](https://radarr.video/): Movie management and download automation.
- [Plex](https://www.plex.tv/): Media server for streaming content to various devices.
- [SABnzbd](https://sabnzbd.org/): Usenet binary downloader.
- [Transmission](https://transmissionbt.com/): BitTorrent client.
- [Jackett](https://github.com/Jackett/Jackett): API support for torrent trackers.
- [NZBHydra2](https://github.com/theotherp/nzbhydra2): Meta search application for Usenet indexers.
- [Overseerr](https://overseerr.dev/): Media request and management tool.
- [NordVPN](https://nordvpn.com/): VPN container for secure network connections.

These components form the foundation of a powerful and versatile media server on your Synology DS220+ NAS.
