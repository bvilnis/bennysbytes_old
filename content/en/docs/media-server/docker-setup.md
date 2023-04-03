---
title: "Setting Up Docker & Docker Compose"
description: "Enabling SSH, installing Docker and Docker Compose, and creating necessary directories."
tags: ["docs"]
weight: 3
draft: true
---

In this section, we will enable SSH access to the Synology NAS, install Docker and Docker Compose, and create the necessary directories for the media server applications.

## Step 1: Enable SSH Access

1. Log in to the DiskStation Manager (DSM) web interface using your administrator account.
2. Open the "Control Panel" and navigate to "Terminal & SNMP."
3. Check the box next to "Enable SSH service" and choose a port number (default is 22).
4. Click "Apply" to save the settings.

## Step 2: Install Docker

1. Open the "Package Center" from the DSM main menu.
2. Search for "Docker" in the search bar and click "Install" to install the Docker package.
3. Once installed, open the "Docker" application from the main menu.

## Step 3: Install Docker Compose

1. Connect to your Synology NAS via SSH using an SSH client (e.g., PuTTY on Windows or the Terminal app on macOS/Linux) and log in with your administrator account.
2. Execute the following command to install the Entware package manager:
```bash
wget -O - http://bin.entware.net/x86-64/Installer.sh | sh
```
3. Once Entware is installed, execute the following command to install Python and pip:
```bash
opkg install python3 python3-pip
```
4. Install Docker Compose using pip:
```bash
pip3 install docker-compose
```

## Step 4: Create Directories for Media Server Applications

1. Open the "File Station" application from the DSM main menu.
2. Navigate to the root of your volume (e.g., `volume1`) and create the following directories:

   - `docker`: This directory will store the configuration files for each container.
   - `media`: This directory will store your media files (movies, TV shows, etc.) and download directories.

3. Inside the `docker` directory, create subdirectories for each media server application:

   - `sabnzbd`
   - `transmission`
   - `jackett`
   - `nzbhydra2`
   - `sonarr`
   - `radarr`
   - `overseerr`
   - `plex`

4. Inside the `media` directory, create the following subdirectories:

   - `downloads`: This directory will store completed downloads from Sabnzbd and Transmission.
     - `incomplete`: This subdirectory within `downloads` will store incomplete downloads from Sabnzbd.
     - `torrents`: This subdirectory within `downloads` will store torrent files for Transmission's watch folder.
   - `movies`: This directory will store movie files.
   - `tv`: This directory will store TV show files.

Your Synology NAS is now prepared for Docker and Docker Compose. In the next section, we will configure the `docker-compose.yml` file to deploy the media server applications.
