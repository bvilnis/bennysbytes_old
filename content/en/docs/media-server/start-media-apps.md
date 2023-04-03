---
title: "Starting the Media Apps"
description: "Using Docker Compose to start the containers and verify their operation."
tags: ["docs", "media-server"]
weight: 6
draft: false
---

## Launching the Media Apps

With the Docker Compose file created, the necessary directories in place, and the `/dev/net/tun` device set up, it's time to start your media server containers.

1. **SSH into your Synology NAS**: If you're not already connected, open a terminal on your local computer and use the `ssh` command to connect to your Synology NAS. Replace `<admin_user>` with your admin username and `<NAS_IP>` with the IP address of your Synology NAS:
```bash
ssh <admin_user>@<NAS_IP>
```

2. **Navigate to the Docker Compose directory**: Move to the directory where you uploaded the `docker-compose.yml` file on your Synology NAS:
```bash
cd /volume1/docker
```

3. **Start the containers**: Run the following command to start the containers defined in your `docker-compose.yml` file:
```bash
sudo docker-compose up -d
```
This command will download the necessary images (if not already downloaded), create the containers, and start them in the background.

4. **Verify container status**: To check that all containers are running correctly, run the following command:
```bash
sudo docker-compose ps
```
This command will show the status of the containers, including their names, state, and exposed ports.

Now, your media server containers should be up and running. You can access each service using the appropriate port and IP address of your Synology NAS.

Here's the list of the apps and their corresponding ports:

* **Sonarr:** `http://<NAS_IP>:8989`
* **Radarr:** `http://<NAS_IP>:7878`
* **SABnzbd:** `http://<NAS_IP>:8080`
* **Transmission:** `http://<NAS_IP>:9091`
* **Jackett:** `http://<NAS_IP>:9117`
* **NZBHydra2:** `http://<NAS_IP>:5076`
* **Overseerr:** `http://<NAS_IP>:5055`
* **Plex:** `http://<NAS_IP>:32400/web`

Replace `<NAS_IP>` with the actual IP address of your Synology NAS.
