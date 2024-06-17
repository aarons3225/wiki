---
title: Linux-Installation
description: How to install Plex on Linux
published: true
date: 2024-06-17T07:01:28.975Z
tags: homelab, linux, self-hosted, plex
editor: markdown
dateCreated: 2024-06-17T07:01:28.975Z
---

# Requirements

- Linux based computer
- Internet connection

> I am using Ubuntu 22.04 and that is what I recommend. Plex does support other versions however. {.is-info}

## Download

Navigate via your browser to [Plex Downloads Page](https://www.plex.tv/media-server-downloads). 

Select the correct version you need and right click and copy address.

- ssh into your server

```sh
ssh USER@HOST
```
- Enter your password

From there, you should be in the home directory which looks like /home/USER

- Enter:

```sh
sudo wget PASTE_THE_COPIED_LINK
enter your sudo password
```

now it is downloaded.

If you want to check, enter:

```sh
ls
```
> If you see somehting like: plexmediaserver_1.40.3.8555-fef15d30c_amd64.deb then you did it correctly {.is-success}

## Install
- From the terminal window:
```sh
sudo dpkg -i plexmediaserver_1.40.3.8555-fef15d30c_amd64.deb
```

That should install it.

## Starting Plex

On most flavors of linux you should be able to start plex with the command:

```sh
sudo systemctl start plexmediaserver
```
> On Ubuntu 22.04, I didn't need this option. Using dpkg -i was enough. {.is-info}

## Accessing Plex

If on your same machine:

- Open a web browser and navigate to http://localhost:32400/web
or
- http://127.0.0.1:32400/web

If on a remote machine:

- Open a web browser and navigate to http://SERVER-IP:32400/web

## Remove the .deb file
- To remove the .deb file, in the same terminal window:

```sh
sudo rm plexmediaserver_1.40.3.8555-fef15d30c_amd64.deb
or
sudo rm *.deb # This option should remove all .deb files
```

