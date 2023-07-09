---
title: "Installing the Media Applications"
description: "Enabling the SynoCommunity package repository, creating necessary directories, and installing media applications."
tags: ["docs", "media-server"]
weight: 4
draft: false
---

## Setting Up SynoCommunity Package Requirements

In this section, we will allow the installation of packages from SynoCommunity, install the media server applications, and create the necessary directories for them.

### Step 1: Allow Installation of SynoCommunity Packages

1. Open the "Package Center" from the DSM main menu.
2. Click on the "Settings" button.
3. In the settings window, switch to the "Package Sources" tab.
4. Click "Add", enter "SynoCommunity" as the Name and "http://packages.synocommunity.com" as the Location.
5. Click "OK" to add the package source.
6. In the "General" tab, set the Trust Level to "Any publisher".

### Step 2: Create Directories for Media Server Applications

1. Open the "File Station" application from the DSM main menu.
2. Navigate to the root of your volume (e.g., volume1) and create the following directories:
   * `media/`: This directory will store your media files (movies, TV shows, etc.) and download directories.
3. Inside the media directory, create the following subdirectories:
   * `downloads/`: This directory will store completed downloads from Sabnzbd and Transmission.
      * `incomplete/`: This subdirectory within downloads will store incomplete downloads from Sabnzbd.
      * `torrents/`: This subdirectory within downloads will store torrent files for Transmission's watch folder.
   * `movies/`: This directory will store movie files.
   * `tv/`: This directory will store TV show files.

When done, your directory structure should look like this:

```
volume1
└── media
    ├── downloads
    │   ├── incomplete
    │   └── torrents
    ├── movies
    └── tv
```

### Step 3: Install Media Server Applications

1. Go back to the "Package Center" in the DSM main menu.
2. In the "Community" tab, you should now see the available packages from SynoCommunity.
3. Install the following packages:
   * Sonarr
   * Radarr
   * SABnzbd
   * Transmission
   * Jackett
   * NZBHydra2
   * Overseerr
   * Plex Media Server.

Here’s the list of the apps and their corresponding ports once they have been installed:

* **Sonarr:** `http://<NAS_IP>:8989`
* **Radarr:** `http://<NAS_IP>:7878`
* **SABnzbd:** `http://<NAS_IP>:8080`
* **Transmission:** `http://<NAS_IP>:9091`
* **Jackett:** `http://<NAS_IP>:9117`
* **NZBHydra2:** `http://<NAS_IP>:5076`
* **Overseerr:** `http://<NAS_IP>:5055`
* **Plex:** `http://<NAS_IP>:32400/web`

{{% pageinfo %}}
Replace `<NAS_IP>` with the actual IP address of your Synology NAS.
{{% /pageinfo %}}

Your Synology NAS is now set up with the necessary media server applications from SynoCommunity and the necessary directories have been created. In the next section, we will configure our Usenet provider and indexer and then move onto configuring these applications.
