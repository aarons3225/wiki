---
title: Swap.img and disk full fix
description: How to fix the swap.img  and disk full
published: true
date: 2024-06-03T10:14:49.487Z
tags: homelab, software, linux, ubuntu
editor: markdown
dateCreated: 2024-06-03T10:14:49.487Z
---

# Reason for post
Plex randomly stopped working. I wondered why? It took me a bit to figure out, but I checked my webmin dashboard and saw that my disk was full. Some playing around and I had high swap.img usage and the ubuntu-lvm volume created at startup was full. So here is my fix below. I view this as how to put that particular fire out, I have not figured out how to stop the fire from happening in the first place. 

# Swap Image
---
I have ran into an issue where the swapfile has become full. I have found a fix to it, but it is to resize it. Swap file basically uses ram so if you don't want to keep giving it more and more and more to the point where you need to upgrade the ram, then what I did was basically delete the swap file and make a new one. 

# How
Log in via ssh or open the terminal:
```sh
sudo swapoff -a
sudo rm swap.img
```

Next go to webmin dashboard, http://ipaddress:10000. Go to System/Disk and Network Filesystems. At the bottom is Virtual Memory. Click on it. 

![webmin1.webp](/webmin1.webp)

It should take you to a Edit Mount page. On the mount now? click mount. on the right, make sure swap file is selected. Click save.

![webmin2.webp](/webmin2.webp)

It should bring you to a page to select file size. Edit it, then click save.

You should be able to check the free space with the command:
```sh
free -m
```

# Disk full
---
Open the webmin dashboard, http://ipaddress:10000, then go to Hardware/Logical Volume Management.

![webmin3.webp](/webmin3.webp)

Click on Logical Volumes

![webmin4.webp](/webmin4.webp)

Click on the disk icon labeled ubuntu-lv with a size of disk below label.

![webmin5.webp](/webmin5.webp)

For volume size, modify that to desired size, then click save.

# Citations
---
Webmin: 
1. main: [https://webmin.com](https://webmin.com)
2. downloads: [https://webmin.com/download/](https://webmin.com/download/)

Ploi.io:
1. [https://ploi.io/documentation/server/change-swap-size-in-ubuntu](https://ploi.io/documentation/server/change-swap-size-in-ubuntu)