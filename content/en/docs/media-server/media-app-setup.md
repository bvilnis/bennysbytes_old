---
title: "Setting Up Media Apps"
description: "Setting up the docker-compose.yml file with the configuration for all media server containers."
tags: ["docs", "media-server"]
weight: 4
draft: true
---

In this section, we will create the `docker-compose.yml` file on your local machine and upload it to the Synology NAS.

The `docker-compose.yml` file sets up a media server environment on a Synology NAS, with various interconnected services to download and manage media content, such as movies and TV shows. The configuration includes the following services:

1. **VPN**: A NordVPN container that provides a secure connection for other services to use. It waits for the `/dev/net/tun` device to be available before starting.
2. **SABnzbd**: A Usenet binary downloader that uses the VPN container for its network connection.
3. **Transmission**: A BitTorrent client that also utilizes the VPN container for its network connection.
4. **Jackett**: A service that provides API access to various torrent trackers, enabling Sonarr and Radarr to search for content on those trackers.
5. **NZBHydra2**: A meta-search application for Usenet indexers, which consolidates multiple sources into a single interface for Sonarr and Radarr to search.
6. **Sonarr**: A TV show management application that can monitor and manage your TV library, search for new episodes, and integrate with SABnzbd, Transmission, Jackett, and NZBHydra2.
7. **Radarr**: A movie management application with similar functionality to Sonarr, but tailored specifically for movies.
8. **Overseerr**: A request management and discovery tool for Plex Media Server that integrates with Sonarr and Radarr.
9. **Plex**: A media server that organizes and streams your media content to various devices.
10. **Watchtower**: A container that periodically checks for updates to the images used by other containers and updates them automatically.

The `docker-compose.yml` file also incorporates custom commands to ensure the `sonarr` and `radarr` containers start only after the VPN container is ready. This setup ensures a secure and efficient environment for managing and accessing media content.

## Steps

1. Open a text editor on your local machine (e.g., Notepad on Windows, TextEdit on macOS, or `vim` on Linux).

2. Copy the contents of the following `docker-compose.yml` file.
```yaml
---
version: '3.8'

services:
  vpn:
    container_name: vpn
    image: azinchen/nordvpn:latest
    cap_add:
      - NET_ADMIN
    devices:
      - /dev/net/tun:/dev/net/tun
    environment:
      - NETWORK=192.168.8.0/24
      - USER=<your_email>
      - PASS=<your_password>
      - COUNTRY=Australia
      - TECHNOLOGY=openvpn_udp
    ports:
      - 8080:8080
      - 9091:9091
      - 51413:51413
      - 51413:51413/udp
    restart: unless-stopped
    # Wait for /dev/net/tun to be available before starting the container
    command: /bin/sh -c "while [ ! -c /dev/net/tun ]; do sleep 30; done; exec /app/start.sh"

  sabnzbd:
    container_name: sabnzbd
    image: linuxserver/sabnzbd:latest
    network_mode: service:vpn
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/sabnzbd:/config
      - /volume1/media/downloads:/downloads
      - /volume1/media/downloads/incomplete:/incomplete-downloads
    restart: unless-stopped

  transmission:
    container_name: transmission
    image: linuxserver/transmission:latest
    network_mode: service:vpn
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/transmission:/config
      - /volume1/media/downloads:/downloads
      - /volume1/media/downloads/torrents:/watch
    restart: unless-stopped

  jackett:
    container_name: jackett
    image: linuxserver/jackett:latest
    ports:
      - 9117:9117
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Sydney/Australia
    volumes:
      - /volume1/docker/jackett:/config
      - /volume1/media/downloads:/downloads
    restart: unless-stopped

  nzbhydra2:
    container_name: nzbhydra2
    image: linuxserver/nzbhydra2:latest
    ports:
      - 5076:5076
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/nzbhydra2:/config
      - /volume1/media/downloads:/downloads
    restart: unless-stopped

  sonarr:
    container_name: sonarr
    image: linuxserver/sonarr:latest
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/sonarr:/config
      - /volume1/media/tv:/tv
      - /volume1/media/downloads:/downloads
    ports:
      - 8989:8989
    restart: unless-stopped
    # Wait for the VPN container to be ready before starting the container
    command: /bin/sh -c "until nc -z -w 5 vpn 8080; do echo 'Waiting for VPN container to be ready...'; sleep 60; done; exec /init"

  radarr:
    container_name: radarr
    image: linuxserver/radarr:latest
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/radarr:/config
      - /volume1/media/movies:/movies
      - /volume1/media/downloads:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped
    # Wait for the VPN container to be ready before starting the container
    command: /bin/sh -c "until nc -z -w 5 vpn 8080; do echo 'Waiting for VPN container to be ready...'; sleep 60; done; exec /init"

  overseerr:
    container_name: overseerr
    image: linuxserver/overseerr:latest
    ports:
      - 5055:5055
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/overseerr:/config
    restart: unless-stopped

  plex:
    container_name: plex
    image: linuxserver/plex:latest
    network_mode: host
    environment:
      - PUID=1026
      - PGID=100
      - PLEX_CLAIM=<your_plex_claim>
      - TZ=Australia/Sydney
    volumes:
      - /volume1/docker/plex:/config
      - /volume1/media/tv:/tv
      - /volume1/media/movies:/movies
    restart: unless-stopped

  watchtower:
    container_name: watchtower
    image: containrrr/watchtower
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    command: --schedule "0 2 * * MON"  # This is set to check for updates every Monday at 2 AM
    restart: unless-stopped
```
Be sure to replace the following placeholders with your actual credentials and values:
   - `<your_email>`: Replace with your NordVPN account email.
   - `<your_password>`: Replace with your NordVPN account password.
   - `<your_plex_claim>`: Replace with your [Plex Claim token](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/).

3. Save the file as `docker-compose.yml` on your local machine.

4. Log in to the DiskStation Manager (DSM) web interface using your administrator account.

5. Open the "File Station" application from the DSM main menu.

6. Navigate to the `/volume1/docker` directory on your Synology NAS.

7. Click the "Upload" button and select the `docker-compose.yml` file you created on your local machine.

Your `docker-compose.yml` file is now ready for deployment. In the next section, we will create the `/dev/net/tun` device, configure the script to ensure it's created on startup, and deploy the media server applications using Docker Compose.
