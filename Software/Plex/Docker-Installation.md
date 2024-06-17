---
title: Docker-Installation
description: How to install Plex Media Server
published: true
date: 2024-06-17T06:01:02.312Z
tags: homelab, self-hosted, plex
editor: markdown
dateCreated: 2024-06-17T05:59:46.000Z
---

# Requirements
- Docker
- Docker Compose V2
- Linux 22.04 or higher
- A plex account

> Docker V2 is the preferred method vs. Docker Run\
I would also recommend installing vs-code or if on a headless server, the web version.{.is-info}

## Install Docker

```sh
sudo apt-get update -y
sudo apt-get install ca-certificates curl -y
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

## Directory

I would recommend you set up a specific folder for docker compose files. Just create a folder for them and then it makes things easier to find. For example:
> /home/$USER$/docker/$SERVICE-NAME$
	> /home/mary/docker/plex(or plexmediaserver) {.is-info}
  
- To do so:
	- Open a terminal and enter:

```sh
pwd
```
Should put you in the /home/$USER directory.

- From there:
```sh
sudo mkdir docker
cd docker
sudo mkdir plex
```

> You should now have created /home/$USER$/docker/plex {.is-success}

In a Tree it should look like:
```
home
	L_USER
  	  L_docker
      		L_plex
```

## Docker Compose
Now you need to create the docker compose file.

To do so:
- In the same terminal so you should be in /home/USER/docker:

```sh
cd plex
sudo docker nano compose.yml
```
> If you have vs-code or the web version, you should be able to open your home folder. From there navigate to the docker folder then to the plex one. You then should be able to right click and choose add file and type compose.yml{.is-info}

- Now paste this into either your compose.yml file:
```yaml
services:
  plex:
    image: plexinc/pms-docker
    container_name: plex
    network_mode: host
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Phoenix
      - VERSION=docker
      - PLEX_CLAIM=$PLEX_CLAIM # Optional
      - NVIDIA_VISIBLE_DEVICES=all # For NVIDIA GPUs
    volumes:
      - ./config:/config
      - /dev/shm/:/transcode
      - /mnt/media:/Media
    devices:
      - /dev/dri:/dev/dri # For NVIDIA GPUs
    env_file: .env # Where you can store your plex claim token
    restart: unless-stopped
```

Save and exit the file. In the terminal it should be CTRL + X, then "y", and hit enter.

> To get your plex token go to [Plex Claim](https://plex.tv/claim). Either replace the $PLEX_CLAIM by pasting over it, or create a .env file the same way you did the compose.yml file. Enter: PLEX_CLAIM=YOURPLEXCLAIMTOKEN, then save and exit. {.is-info}

## To Start It Up

In the terminal, you should be in the /home/USER/docker/plex folder. Enter:

```sh
sudo docker compose up -d # the 'd' flag is to run it as a daemon
```

> You just installed Plex!!!\
You should now be able to navigate to http://localhost:32400/web to accesst it and begin adding your media files. If remoting into a headless server, navigate to http://YOUR-IP:32400/web. {.is-success}