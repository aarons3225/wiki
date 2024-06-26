---
title: Plex
description: Your introduction to Plex Media Server
published: true
date: 2024-06-17T07:42:15.921Z
tags: homelab, self-hosted, plex
editor: markdown
dateCreated: 2024-06-17T06:02:58.854Z
---

![plex_banner.jpg](/plex_banner.jpg)
# Intro
Plex is the primary reason behind my homelab. Do you enjoy relaxing at home and watching a movie? Maybe a TV Show? Well how do you do it? Amazon prime? Netflix? Blu-ray?  Do you have subscriptions to all of those? 

The cost can add up and you don’t really own anything. Sometimes those services remove your favorite movie or show. Then what? 

# What is plex?
Plex has two applications. The server and the client.

Plex media server is an application that allows you to point the application to a directory of media files. The application then serves those media files up to a client. 

Plex has apps for about every device. Your phone, tablet, Apple TV, Xbox, etc. This allows you to play the files that your plex media server is pointing to. These apps are clients.

When you download Netflix for example, it is acting as a client to the Netflix servers that serve all the content they offer that is stored on many many hard drives. Plex does the same thing but for your own home using your own hardware and content you own at a smaller scale.

# Features
Plex has many features. A couple that are very convenient are:

1. Remote connection: this means that plex content can be viewed on a mobile device not on your home network. You can stream your favorite movies or shows you own while on the go.
2. Metadata matching: this means it will pull information from the internet to give you details about the movie or show including posters, descriptions, cast, etc. 
3. Offline viewing: this means that you can download the media directly to your device similar to how other services will let you to view when you don’t have a data connection i.e. on a plane. 
4. DVR: plex allows you to connect a tuner to your server to record live tv and view it later like TiVO. 

# Connecting other services
Now I’ve mention in other posts about services like radarr and sonarr. Both of those are media library management software for movies and shows respectively. They can move your library en mass, keep track of series i.e. John Wick, rename your files, etc. 

Renaming of files is perhaps the biggest reason for utilizing the services. Plex has a particular naming scheme to utilize the metadata matching. That’s why I am including those services here in this post. It’s an important piece that helps tie in the reason for having them in the first place. 

# Installation

- [Docker-Installation](/Software/Plex/Docker-Installation)
- [Linux-Installation](/Software/Plex/Linux-Installation)


#### For Client Side Apps
- iOS
	- [Plex App](https://apps.apple.com/us/app/plex-watch-live-tv-and-movies/id383457673)
  - [Plexamp](https://apps.apple.com/us/app/plexamp/id1500797510)
  - [Plex Dash](https://apps.apple.com/us/app/plex-dash/id1500797677)
  - [Infuse](https://apps.apple.com/us/app/infuse-video-player/id1136220934)
- MacOS
	- [Plex](https://downloads.plex.tv/plex-desktop/1.94.1.155-f1e7f457/macos/Plex-1.94.1.155-f1e7f457-universal.zip?_gl=1*lrhtbp*_gcl_au*MTY1OTc2MzU0Ni4xNzE4NTE3MzIx*_ga*Njg0ODUwNzkzLjE3MTg1MTczMjE.*_ga_G6FQWNSENB*MTcxODYwOTc2Ny40LjEuMTcxODYwOTc2OS41OC4wLjA.)
  - [Infuse](https://apps.apple.com/us/app/infuse-video-player/id1136220934)
- TvOS
	- Open the apps and search for the plex or infuse. 
- Plus many more for other clients like android, nvidia shield, etc. etc. 

# Updating

Check out this updating script on my other post [HERE](/Software/Plex/Update-Plex-Script).