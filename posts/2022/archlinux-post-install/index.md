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
If you've followed my part one, you are probably in a black background with white bash prompt. Feel free to login with your username, 'root' and your root's password. Now let's check our system a bit,

### Intenet
Check your internet connection with ping,
```bash
ping 1.1.1.1
```

> Tip: **Ctrl + c** to stop a process

And it should work out of the box for Ethernet. This process is as same as installation of Arch Linux (part one). If you encounter any problem, check `NetworkManager` 's status with,
```bash
systemctl status NetworkManager
```

If it's disabled, you can enable and start with, `systemctl enable` and `systemctl start` command or just rebooting your system.

### Boot time
Try, `systemd-analyze` to print your boot time. If your boot time is less than 15 seconds, you can check Arch wiki for performance guideline. 

>With an old HDD, my boot time was around 11 seconds.

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

## Packages

### Officail packages
Arch has a great collection of free and open source software. And they are quite strict about their collection. You can browse through them from here,
- [Official repositories - ArchWiki](https://wiki.archlinux.org/title/Official_repositories) 

### AUR
AUR means **Arch User Repository**. It contains more packages than the official one and undoubtedly one of the main reason for a lot of people to actually use Arch Linux. Learn more about it from here,
- [Arch User Repository - ArchWiki](https://wiki.archlinux.org/title/Arch_User_Repository)

Installing a AUR packages are rather simple! You can also use AUR helpers which do the job in the background so that you don't have to make your hands dirty. Now `yay` and `paru` AUR helpers are quite popular.

To install an AUR package git clone it and then build it with `makepkg` or directly build and install with `makepkg -si`. 

### Third party repo
If you've used AUR then you may know how time consuming certain builds can be. Some AUR packages even take several hours for example browsers. That's where third party repository comes in. One of the popular one is `chaotic-AUR`. They build packages automatically and put the binary in a hosting service so that you don't have to build manually.

### Chaotic AUR
Once you install `chaotic-AUR` you can just use your pacman to install from chaotic AUR. To setup `chaotic AUR` you can go to it's [official website](https://aur.chaotic.cx/) and follow along. Or run this script, it'll do the job for you(made by me). Just open terminal and run,
```bash
wget -q -O chaotic-AUR-installer.bash https://raw.githubusercontent.com/SharafatKarim/chaotic-AUR-installer/main/install.bash && sudo bash chaotic-AUR-installer.bash && rm chaotic-AUR-installer.bash
```

## Package management
### Pacman
Arch linux use `pacman` to mange it's packages. It's really good and fast. You can learn about it with more details in the archwiki.
- [pacman - ArchWiki](https://wiki.archlinux.org/title/Pacman)
- [pacman/Tips and tricks - ArchWiki](https://wiki.archlinux.org/title/Pacman/Tips_and_tricks) 

And for quick reference, you can check my handy reference,
- [Pacman package manager](https://sharafat.vercel.app/pacman-package-manager) 

And for configuration, you can set mirror just like you did in the arch installation process (part one),
#### Reflector
With reflector you can easily set a mirror. To do that, first let's make sure our package list is with sync with server by,
```bash
pacman -Sy
```

then, let's install reflector,
```bash
pacman -S reflector
```

then, you can use reflector to generate a mirrolist. Here's an example,

> My country is Bangladesh so I can display my available local mirrors in this way,
> 
> ```bash
> reflector -c BD
> ```
> 
> and, I can save this list to my mirrorlist in this way,
> 
> ```bash
> reflector -c BD --save /etc/pacman.d/mirrorlist
> ```

#### Manually mirror setup
We can use a text editor to edit the **mirrorlist** and set our desired mirrors also. To do that, you can use nano or vim text editor or install any CLI-based text editor if you need. And there's an online arch mirror list generator,
- [Arch Linux - Pacman Mirrorlist Generator](https://archlinux.org/mirrorlist/)

Simply edit the `mirrorlist` file, like,
```bash
nano /etc/pacman.d/mirrorlist
```

### Colored pacman
And another thing, you can actually make pacman's output colored! To do so, just edit the `/etc/pacman.conf` file and un-comment the line `Color` (removing `#` from a line),
```bash
# Misc options
#UseSyslog
Color ## 33'th line (default)  
#NoProgressBar
```

### Yay
Yay is mainly an AUR helper, that can install AUR packages automatically. And you can install it from `chaotic-aur` or `aur`. If you're downloading from `aur`, then perhaps you can go with `yay-bin` which is a binary of yay. So you don't have to wait for it to finish installation.

If you've installed `chaotic-aur`, then install yay with,
```bash
sudo pacman -S yay
```

Or, if you wish to install from AUR, try in this way,
```bash
pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```

{{< admonition "tip" >}}
If your pacman is colored then so will be your yay or paru AUR helper
{{< /admonition >}}

### Pamac
Pamac is a graphical installer for pacman with AUR support. And it can help you to install dependency packages much more easily. With sorting you can also list you orphaned packages or other packages into different categories. So if you wish to use pamac, you can install it from chaotic AUR, or from AUR.

If you've yay installed, then you can use it now in this way,
```bash
yay -S pamac-aur
```

## Shell
By default your shell is `bash`. And you can enhance your possibilities with an another shell like `zsh` or `fish`. You can also do a lot with your `.bashrc` file. If you're looking for a nice beautiful `zsh` shell with useful plugins like, auto coloring, auto completion then I've a separate tutorial for you.
- [Zsh and antigen](/zsh-and-antigen/)

And if you need a template for `bashrc` or `zshrc` then, I've it for you,
- [bashrc template](https://sharafat.vercel.app/bashrc)

## Timeshift
Now you may want to take snapshots, right? Let's install `timeshift`. If you're installing from AUR then perhaps the binary version?

### timeshift-autosnap
`timeshift-autosnap` package will trigger timeshift to take a snap everytime when pacman upgrades your system. Just install it! Available in both chaotic AUR or AUR.

To configure it, use `/etc/timeshift-autosnap.conf`. But default configuration should be enough! You can test it with,
```bash
sudo timeshift-autosnap
```

## GRUB

### grub-btrfs
It'll add btrfs snapshots in your GRUB boot options. To use, install `grub-btrfs`. And regenerate the `grub.cfg` with,
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```


### GRUB timeout
### Info screen after grub
When you system starts first comes grub, and then? Something like, stating linux-zen-...., right? And do you remember when you were installing arch, while booting you say some green and white combination type progress like interface. You can actually toggle them. You have to remove a kernel parameter, called `quiet`.

To edit kernel parameters, edit `/etc/default/grub`.
And regenerate the `grub.cfg` with,
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

## Extra partitions
Besides we'll have to mount our extra **disk partitions** as well and for that purpose we'll add NTFS support. So install `ntfs-3g`. And now you can mount ntfs partitions with `sudo mount` but it's not an idea solution. To make changes permanently you've to edit `fstab`.

### swap partition
Our swap partition should work out of the box if you've followed my part one of this arch install post. To verify, run, `swapon` or, `free -h`.
If you need swap file or, maybe an another swap partition or you didn't follow my guide, check this guide from manjaro. It's good to follow,
- [Swap - Manjaro](https://wiki.manjaro.org/index.php/Swap) 

Also check out the `systemd-swap`, it's even better choice, I think instead of tradition swap, if you want.

### Other partitions
If you want you can easily set other partitions to mount by default with the help of  `partitionmanager` or `gnome-disk-utility` and it's recommend to avoid errors. You can also edit `fstab` manually.

#### KDE partition manager
It's recommended to use `/mnt` directory. If you want you can create a sub directory inside first with,
```bash
sudo mkdir /mnt/data
```
Later launch kde partition manager, select your partition. From the right click menu, select `Edit mount point` and select the path `/mnt/data`. Finally click ok and 

#### Gnome Disk Utility


## Performance
## nohang
A low ram handler. First install `nohang` from AUR or chaotic AUR. It can prevent OOM(Out of Memory). Learn more [here](https://github.com/hakavlad/nohang).
Start and enable `nohang.service` or `nohang-desktop.service` after installing,
```bash
sudo systemctl enable --now nohang-desktop.service
```

> `nohang-desktop` provides notification when you're almost out of memory.

## Plasma Specials

### Spell check
Make sure `sonnet` is installed with `hunspell` or anything similar.

### Fonts
To enhance performance for terminal and other places you might want to Install `noto-sans` optional dependency, especially for `emoji-picker`.

If you face problem in default terminal and othere monospace fonts, try installing `ttf-dejavu` and `ttf-liberation`.
