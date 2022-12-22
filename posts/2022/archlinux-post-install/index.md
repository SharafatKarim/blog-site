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

Then, I'll un-comment the line (removing `#` from a line),
```bash
## Uncomment to allow members of group wheel to execute any command  
%wheel ALL=(ALL:ALL) ALL
```

> In `nano` text editor you can use `ctrl + w` to search. Then press, `ctrl + o` to save, followed by an `enter` and then `ctrl + x` to exit.

## Minimal Plasma
Now in this post, I'll be installing minimal KDE plasma desktop environment without any bloat or any extra packages! So that if you need further packages or services like bluetooth or printer support, you can do it later. And of course, instead of plasma, you can try anything else like, gnome, xfce or maybe a window manager!

To install minimal plasma, try,
```bash
pacman -S plasma-desktop
```

Now, it'll give you several choices. You can go with the default values. For font you can choose, `noto-sans` and as a back-end for media thumbnail in the file manager, you can try `vlc` as it's recommended by upstream developers.


## Plasma essentials
Besides a browser, for convenience we'll install our favorite file manager and terminal utilities. And if you're going for plasma we'll also try some plasma integrations like, network manager support and kde plasmoids.

Let's let it install and let me describe what they are,
```bash
pacman -S firefox plasma-nm plasma-pa dolphin konsole kdeplasma-addons kde-gtk-config plasma-systemmonitor spectacle
```

And here's a short description,
| Application name     | Application's description                                                                                                                                          |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| firefox              | A FOSS browser, which is favorite to a lot of linux users and you can also customize it with CSS. But of course you can also use anything else that you prefer.    |
| plasma-nm            | Network manager integration with plasma. With this you can easily configure network with your plasma desktop.                                                      |
| plasma-pa            |                                                                                                                                                                    |
| dolphin              | A file manger for plasma. It's really recommended because of it's availability, user interface and a lot of features out of the box.                               |
| konsole              | A terminal app for plasma. It's highly configurable through GUI and easy to integrate with plasma.                                                                 |
| kdeplasma-addons     | **[OPTIONAL]** Extra addons like color picker and monitor.                                                                                                         |
| kde-gtk-config       | It'll allow you to customize gtk apps through kde's setting and recommended to install                                                                             |
| plasma-systemmonitor | **[OPTIONAL]** It's a nice looking system monitor that you may want to try. You can also avoid it if you're happy with `htop` or anything else                     |
| spectacle            | **[OPTIONAL]** It's a screenshot taking utility from kde plasma and highly recommended as it has annotation a lot of automated abilities with plasma's integration | 

## SDDM
For plasma's login manager we'll use SDDM, as you can integrate it with plasma's setting. If you want you can also try **lightdm** or anything you like. To install SDDM, try,
```bash
pacman -S sddm sddm-kcm
```

> `sddm-kcm` is only recommended when you're installing plasma. It'll integrate your sddm  with kde's setting. So you can customize your sddm right from kde plasma's setting.

And the enable it's service with,
```bash
systemctl enable sddm
```

And finally, start it with,
```bash
systemctl start sddm
```

Now you'll be greeted with a default login window. Feel free to login with your created user.

## Third party repository and AUR
We'll also see an interesting project, named 'chaotic AUR' along with AUR helpers (both CLI and GUI). Because you may want to intall timeshift.

## Extra partitions
Besides we'll mount our extra **disk partitions** as well and for that purpose we'll add NTFS support. 