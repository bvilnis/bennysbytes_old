---
title: "Configuring the Media Applications"
description: "Basic configuration of each media server application, such as Sonarr, Radarr, and Plex."
tags: ["docs", "media-server"]
weight: 5
draft: false
---

## Configuring the Media Server Applications

Now that the applications are installed and running, you'll need to configure each application to work seamlessly with each other. Follow the steps below to set up each application:

### 1. Jackett

1. Access Jackett by visiting `http://<NAS_IP>:9117`.
2. [Add and configure your preferred torrent indexers.](https://github.com/Jackett/Jackett/wiki/Definition-format)

### 2. NZBHydra2

1. Access NZBHydra2 by visiting `http://<NAS_IP>:5076`.
2. [Configure your Usenet indexers (NZBGeek).](https://github.com/theotherp/nzbhydra2/wiki/Tutorial-(Indexers,-newznab,-API,-*arr,-etc.))
3. [Configure your torrent indexers (Jackett).](https://github.com/theotherp/nzbhydra2/wiki/Tutorial-(Indexers,-newznab,-API,-*arr,-etc.)#torrent-trackers-and-torznab)
4. [Set up search settings for Sonarr and Radarr.](https://github.com/theotherp/nzbhydra2/wiki/Tutorial-(Indexers,-newznab,-API,-*arr,-etc.))

### 3. Transmission

1. Access Transmission by visiting `http://<NAS_IP>:9091`.
2. Configure your torrent settings as needed.
3. Set up watch directory: `/watch`.

### 4. SABnzbd

1. Access SABnzbd by visiting `http://<NAS_IP>:8080`.
2. Go through the initial setup wizard.
3. [Configure your Usenet provider settings.](https://sabnzbd.org/wiki/configuration/3.7/servers)
4. [Set up categories and paths for Sonarr and Radarr.](https://sabnzbd.org/wiki/configuration/3.7/categories)

### 5. Sonarr

1. Access Sonarr by visiting `http://<NAS_IP>:8989`.
2. Go through the initial setup wizard.
3. [Configure your download clients](https://wiki.servarr.com/sonarr/settings#download-clients) (SABnzbd and Transmission).
4. [Set up indexers](https://wiki.servarr.com/sonarr/settings#indexers) using Jackett and/or NZBHydra2.
5. [Configure your TV library location:](https://wiki.servarr.com/sonarr/settings#root-folders) `/tv`.

### 6. Radarr

1. Access Radarr by visiting `http://<NAS_IP>:7878`.
2. Go through the initial setup wizard.
3. [Configure your download clients](https://wiki.servarr.com/radarr/quick-start-guide#download-clients) (SABnzbd and Transmission).
4. [Set up indexers](https://wiki.servarr.com/radarr/quick-start-guide#indexers) using Jackett and/or NZBHydra2.
5. [Configure your movie library location:](https://wiki.servarr.com/radarr/quick-start-guide#root-folders) `/movies`.

### 7. Overseerr

1. Access Overseerr by visiting `http://<NAS_IP>:5055`.
2. Go through the initial setup wizard.
3. [Connect your media server (Plex)](https://docs.overseerr.dev/using-overseerr/settings#plex) and your [media management applications (Sonarr and Radarr)](https://docs.overseerr.dev/using-overseerr/settings#radarr-sonarr-settings).

### 8. Plex

1. Access Plex by visiting `http://<NAS_IP>:32400/web`.
2. Go through the initial setup wizard.
3. [Add your media libraries](https://support.plex.tv/articles/200288926-creating-libraries/) (TV shows and movies) using the appropriate paths: `/tv` and `/movies`.

{{% pageinfo %}}
Don't forget to replace `<NAS_IP>` with the actual IP address of your Synology NAS.
{{% /pageinfo %}}

## Exploring Additional Settings

While the above steps will get your media server up and running, each application has a multitude of settings that can be fine-tuned to meet your specific needs. Here are a couple of areas you might want to explore further:

### Sonarr and Radarr

Both Sonarr and Radarr have advanced settings for controlling the quality and size of the media files you download. For example, you might want to specify that you only want 1080p content, or that you want to limit the file size of your downloads to conserve disk space.

* [Quality Settings in Sonarr](https://wiki.servarr.com/sonarr/settings#quality)
* [Profiles in Sonarr](https://wiki.servarr.com/sonarr/settings#profiles)
* [Quality Settings in Radarr](https://wiki.servarr.com/radarr/settings#quality)
* [Profiles in Radarr](https://wiki.servarr.com/radarr/settings#profiles)

Take some time to explore these and other settings in each application to ensure you're getting the most out of your media server. Remember, part of the fun of having your own media server is tailoring it to work exactly the way you want!
