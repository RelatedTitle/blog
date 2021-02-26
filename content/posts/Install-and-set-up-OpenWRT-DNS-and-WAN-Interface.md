---
title: How to install and set up OpenWRT, DNS, and a WAN Interface.
tags:
- OpenWRT
- DNS
- WAN
- Tutorial
date: 2019-11-23T00:00:00.000+00:00
lastmod: 2021-02-25T00:00:00.000+00:00
description: 'In this tutorial, I will show you how to set up OpenWRT, DNS, and a
  WAN interface. '
image: ''
unlisted: false

---
In this tutorial, I will show you how to set up OpenWRT, DNS, and a WAN interface. Before we begin, you should be aware that any firmware changes you do to your device might brick it. If you are technically knowledgable and assume the risks, continue on with the tutorial. Also, note that OpenWRT recommends at least 4MB storage and 32 MB RAM.

## What is OpenWRT?

OpenWRT is a custom router firmware that allows much more customization than with default router firmware. It allows the user to access advanced router configuration options and install custom software add-ons. OpenWRT is one of the most customizable router firmwares out there. OpenWRT is compatible with many of the popular networking brands.

## How to set it up.

Time needed: 10 minutes.

How to Install and Set Up OpenWRT with DNS and a WAN Interface.

### 1. Verify your router can run OpenWRT.

Before we do anything, we need to verify that your router is able to run OpenWRT. OpenWRT recommends at least 4 MB storage and 32 MB RAM for the newest (18.06 at the time of writing) version. Your router might be able to run OpenWRT without meeting these specs, but it is not recommended. We also need to verify that there is a specific version for your router. All routers are different, so it is important that you get your router’s image. [Check if there’s an image for your router here](https://openwrt.org/toh/views/toh_fwdownload?dataflt%5B0%5D=supported%20current%20rel_%3D18.06.5). OpenWRT supports (among many others) many models from TP-Link, Netgear, Asus, and Linksys,

### 2. Download your router’s OpenWRT image.

We will now download your router’s OpenWRT image, go to [this link](https://openwrt.org/toh/views/toh_fwdownload?dataflt%5B0%5D=supported%20current%20rel_%3D18.06.5). To find the version of your router, scroll down till you see a table with some input fields. Input your router’s brand and model onto the field and hit enter. Now click on the download link in your router’s row at the very right of the table.

### 3. Flash the image on your router.

To correctly install OpenWRT you need to flash the image on your router. Due to every router having different interfaces, I can’t go into detail on how to do this. It is commonly found in the router’s web interface under “Maintenance”, “Firmware Upgrade”, or “Backup and Restore”. If you can’t seem to find any of these, Googling your router’s brand and model along with “flashing firmware” may help you. Once you found it, upload the firmware image and wait till it installs.

### 4. Enter your router’s web interface (LuCI)

Once you have finished installing OpenWRT, you need to set it up. To do this, type “192.168.1.1” (Default router gateway IP) on a web browser and hit enter. You will see a screen prompting you to log in, if not already filled out, type root in the username field and click Login. You will see a screen with a notice prompting you to change your password, we will do this later.Login screen in the LuCI OpenWRT web interface.

### 5. Set up your router to access the internet and DNS.

Right now your router won’t be able to access the internet to fix this we need to do some changes to the LAN interface. Hover over Network in the top bar and click on interfaces, look for the first LAN interface and click edit. Look for IPv4 address box, the default is 192.168.1.1 you need to change this to something other than 192.168.1.\*, I recommend 192.168.10.1. This will change the gateway IP to the one you chose too. Click Save and Apply, you will notice that it won’t “save” the changes and will try to revert, this is normal and it happens because the browser loses connection to the router due to it changing its IP address. Optionally, if you want to change the DNS, scroll down a little till you see the input boxes, and add your DNS there, if you don’t know what to use but want to speed up your DNS requests and make them anonymous, I recommend either Google’s DNS servers (8.8.8.8 and 8.8.4.4) or CloudFlare’s DNS servers (1.1.1.1), both are really good.

### 6. Setting up WAN.

You will have to first head over to the router’s new IP address that you previously changed. Head over to Network -> Interfaces and click edit on the one with the SSID named “OpenWRT”, from there, fill out information like the SSID you will want to have, password, etc. On “Interface Configuration” look for “Network”, make sure LAN is selected, click enable at the top and then save and apply.

### 7. Adding a password to the LuCI (Web Interface)

Adding a password is one of the most important things you should do when setting up a router, this prevents bad actors that are already connected to your internet to be able to modify settings, to do this go to System > Administration and set up your password.

That’s it, those are all the steps needed to properly install and set up OpenWRT, enjoy the added functionality and advanced configuration options added to your router. If you have any problems or questions, feel free to leave them in the comments section.