---
title: "Archlinux Post Install"
date: 2022-12-20T18:38:11+06:00
lastmod: 2022-12-20T18:38:11+06:00
draft: true
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: ""
license: ""
images: []

tags: []
categories: []
summary: ""

featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  maxShownLines: 50
math:
  enable: false
  # ...
mapbox:
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # located in "assets/"
    # Or
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # located in "assets/"
    # Or
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
  # ...
license: '<a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>'
---

## Introduction

This is the continuation of the Arch Linux installation's part one. In the part one, we've installed Arch with as less afford as possible. In this part we'll install from desktop environment to our GRUB setup with BTRFS snapshots integration and a lot of possibilities!

## Prerequisite
If you've followed my part one, you are probably in a black background with white bash prompt. Feel free to login with your username, 'root' and your root's password.

## User Management
To learn deeply about user management's I would recommend you to read the arch wiki. For now, I'll create a user with root privileges so that I don't have to stay in root. Later after installing KDE plasma desktop, I can mange users in the system setting, so, for now let's create a user.
```bash
useradd -m -G wheel arch
```

>Here, `-m` to create a home directory. And if it exists then it won't be overwritten. And the `-G` flag is to set a group. Here `wheel` group users can actually run `sudo` commands. And finally `arch` is my username.

Now, let's set a password for our new user, `arch`,
```bash
passwd arch
```

Now we've to give access to wheel group users to actually able to run `sudo` commands, to do so, edit a file with the following command,
```bash
EDITOR=nano visudo 
```

> Here, nano is the text editors name. Feel free to use your favorite text editor.

Then, 

## Minimal Plasma
Now in this post, I'll be installing minimal KDE plasma desktop environment without any bloat or any extra packages! So that if you need further packages or services like bluetooth or printer support, you can do it later. And of course, instead of plasma, you can try anything else like, gnome, xfce or maybe a window manager!

To install minimal plasma, try,
```bash
pacman -S plasma-desktop
```

## SDDM
For plasma's login manager we'll use SDDM, as you can integrate it with plasma's setting. If you want you can also try **lightdm** or anything you like.

## Plasma essentials
Besides a browser, for convenience we'll install our favorite file manager and terminal utilities. Besides we'll mount our extra **disk partitions** as well. And if you're going for plasma we'll also try some plasma integrations like, network manager support and kde plasmoids.

## Third party repository and AUR
We'll also see an interesting project, named 'chaotic AUR' along with AUR helpers (both CLI and GUI). Because you may want to intall timeshift.