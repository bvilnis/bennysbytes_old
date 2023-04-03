---
title: "Create VPN Tunnel Device"
description: "Configuring the Synology NAS to create the /dev/net/tun device on startup."
tags: ["docs", "media-server"]
weight: 5
draft: false
---

## Creating the /dev/net/tun Device

The NordVPN container requires a `/dev/net/tun` device to function properly. This device may not be created by default on your Synology NAS. To create the device, follow these steps:

1. **Enable SSH Access**: Log in to your Synology NAS's web interface. Go to Control Panel > Terminal & SNMP > Terminal, and check the box to "Enable SSH service." Remember the port number displayed (default is 22).

2. **SSH into your Synology NAS**: Open a terminal on your local computer and use the `ssh` command to connect to your Synology NAS. Replace `<admin_user>` with your admin username and `<NAS_IP>` with the IP address of your Synology NAS:
```bash
ssh <admin_user>@<NAS_IP>
```

3. **Create the /dev/net/tun Device**: Run the following command to create the `/dev/net/tun` device:
```bash
sudo mkdir -p /dev/net && sudo mknod /dev/net/tun c 10 200
```

4. **Make the /dev/net/tun Device Persistent**: To ensure the `/dev/net/tun` device is created automatically after a reboot, you need to create a task in the Synology NAS's Task Scheduler.

- Go to Control Panel > Task Scheduler and click on "Create" > "Triggered Task" > "User-defined script."
- Enter a Task name, such as "CreateTunDevice."
- Set the "User" to "root."
- Under the "Task Settings" tab, enter the following script in the "Run command" field:

  ```bash
  mkdir -p /dev/net && mknod /dev/net/tun c 10 200 && chmod 0666 /dev/net/tun
  ```

- Go to the "Trigger" tab and select "At boot up" as the trigger.
- Click "OK" to save the task.

Now, your Synology NAS will create the `/dev/net/tun` device automatically after every reboot, ensuring the VPN container functions properly.
