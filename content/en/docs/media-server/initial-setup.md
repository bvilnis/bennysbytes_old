---
title: "Initial Synology NAS Setup"
description: "Instructions for setting up the Synology NAS for the first time, including configuring the storage and basic settings."
tags: ["docs", "media-server"]
weight: 2
draft: false
---

## Intial Setup for the Synology NAS

In this section, we will walk through the process of setting up the Synology DS220+ NAS for the first time. This includes configuring the storage, network settings, and installing the DiskStation Manager (DSM) operating system.

### Step 1: Install Hard Drives

1. Power off the Synology NAS and unplug it from the power source.
2. Open the front cover by gently pulling it away from the device.
3. Remove the drive trays by pressing the tabs on both sides and sliding them out.
4. Attach the Seagate Ironwolf NAS 10TB hard drives to the drive trays using the provided screws.
5. Insert the drive trays back into the Synology NAS and close the front cover.
6. Connect the Synology NAS to your network using an Ethernet cable and plug it into a power source.

### Step 2: Install DiskStation Manager (DSM)

1. Power on the Synology NAS and wait for it to boot up.
2. On a computer connected to the same network, open a web browser and visit [find.synology.com](find.synology.com). The Synology Web Assistant should appear and detect your NAS.
3. Follow the on-screen instructions to install DiskStation Manager (DSM) on your Synology NAS.
4. Once DSM is installed, you'll be prompted to create an administrator account.

### Step 3: Configure Storage

1. Log in to the DSM web interface using your administrator account.
2. Open the "Storage Manager" application from the DSM main menu.
3. Navigate to the "Volume" tab and click "Create" to create a new volume.
4. Follow the Volume Creation Wizard to set up your storage pool and volume using the JBOD (Just a Bunch Of Disks) configuration for combined storage space without data protection.

### Step 4: Update DSM and Install Essential Packages

1. In the DSM web interface, open the "Control Panel" and navigate to "Update & Restore."
2. Update DSM to the latest version by clicking "Download" and then "Update Now."
3. Once the update is complete, open the "Package Center" from the DSM main menu.
4. Install essential packages such as "File Station and "Universal Search" by clicking "Install" for each package.

Your Synology DS220+ NAS is now set up and ready for further configuration. In the next section, we will prepare the necessary requirements for using Usenet.
