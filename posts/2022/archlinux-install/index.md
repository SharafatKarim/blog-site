---
title: "Archlinux minimal Install with btrfs"
date: 2022-12-19T15:25:33+06:00
lastmod: 2022-12-19T15:25:33+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: "A complete guide to install Arch Linux with btrfs, linux zen kernel and minimal kde plasma with advace snapshot support!"
license: ""
images: []
resources:
- name: "featured-image"
  src: "featured.jpg"

tags: ['linux', 'os', 'tutorial', 'arch', 'kde', 'btrfs', 'plasma']
categories: ['tutorial']
summary: "A complete guide to install Arch Linux with btrfs, linux zen kernel and minimal kde plasma with advace snapshot support! (part one)"

featuredImage: "featured-image"
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

If you don't know about Arch Linux, and willing to learn, then check this post,
- [Arch Linux](https://wiki.archlinux.org/title/Arch_Linux)

In this guide I'll be installing Arch Linux with BTRFS. And [in a separate article](/archlinux-post-install/) I'll show you the way to a minimal KDE plasma desktop along with some extended possibilities. If you're reading this I can assume you are already familiar with [archwiki](https://wiki.archlinux.org/) - a great place to learn about Arch Linux!

{{< admonition tip >}}
This post will be long and may be hard to navigate without TOS (table of contents). So please use table of contents. On desktop it's placed on the right side and mobile device users can access it from the very top of the post.
{{< /admonition >}}

## Why Arch?

If you don't have much idea about different distros, maybe you can read this [article](https://wiki.archlinux.org/title/Arch_compared_to_other_distributions). Also you'll find a lot of guys in YouTube for this purpose (to explain you why you need arch). If you've much free time to tinker with your system and you are in need of a full time job with no salary, welcome to the arena! I'll highly recommend you to try Arch Linux. 

{{< admonition question "F.A.Q.'s" false >}}
From [ArchWiki](https://wiki.archlinux.org/title/Frequently_asked_questions)
-   [1 General](https://wiki.archlinux.org/title/Frequently_asked_questions#General)
    -   [1.1 What is Arch Linux?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_is_Arch_Linux?)
    -   [1.2 Why would I not want to use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_would_I_not_want_to_use_Arch?)
    -   [1.3 Why would I want to use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_would_I_want_to_use_Arch?)
    -   [1.4 What architectures does Arch support?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_architectures_does_Arch_support?)
    -   [1.5 Does Arch follow the Linux Foundation's Filesystem Hierarchy Standard (FHS)?](https://wiki.archlinux.org/title/Frequently_asked_questions#Does_Arch_follow_the_Linux_Foundation's_Filesystem_Hierarchy_Standard_(FHS)?)
    -   [1.6 I am a complete GNU/Linux beginner. Should I use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_am_a_complete_GNU/Linux_beginner._Should_I_use_Arch?)
    -   [1.7 Is Arch designed to be used as a server? A desktop? A workstation?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_Arch_designed_to_be_used_as_a_server?_A_desktop?_A_workstation?)
    -   [1.8 I really like Arch, except the development team needs to implement feature X](https://wiki.archlinux.org/title/Frequently_asked_questions#I_really_like_Arch,_except_the_development_team_needs_to_implement_feature_X)
    -   [1.9 When will the new release be made available?](https://wiki.archlinux.org/title/Frequently_asked_questions#When_will_the_new_release_be_made_available?)
    -   [1.10 Is Arch Linux a stable distribution? Will I get frequent breakage?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_Arch_Linux_a_stable_distribution?_Will_I_get_frequent_breakage?)
    -   [1.11 Arch needs more press (i.e. advertisement)](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_more_press_(i.e._advertisement))
    -   [1.12 Arch needs more developers](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_more_developers)
-   [2 Installation](https://wiki.archlinux.org/title/Frequently_asked_questions#Installation)
    -   [2.1 Arch needs an installer. Maybe a GUI installer?](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_an_installer._Maybe_a_GUI_installer?)
    -   [2.2 I installed Arch, and now I am at a shell! What now?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_installed_Arch,_and_now_I_am_at_a_shell!_What_now?)
    -   [2.3 Which desktop environment or window manager should I use?](https://wiki.archlinux.org/title/Frequently_asked_questions#Which_desktop_environment_or_window_manager_should_I_use?)
    -   [2.4 What makes Arch unique amongst other "minimal" distributions?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_makes_Arch_unique_amongst_other_"minimal"_distributions?)
-   [3 System maintenance](https://wiki.archlinux.org/title/Frequently_asked_questions#System_maintenance)
    -   [3.1 Why is my internet so slow compared to other operating systems?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_my_internet_so_slow_compared_to_other_operating_systems?)
    -   [3.2 Why is Arch using all my RAM?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_Arch_using_all_my_RAM?)
    -   [3.3 Where did all my free space go?](https://wiki.archlinux.org/title/Frequently_asked_questions#Where_did_all_my_free_space_go?)
-   [4 Package management](https://wiki.archlinux.org/title/Frequently_asked_questions#Package_management)
    -   [4.1 I have found an error with package X. What should I do?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_have_found_an_error_with_package_X._What_should_I_do?)
    -   [4.2 Arch packages need to use a unique naming convention. ".pkg.tar.zst" is too long and/or confusing](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_packages_need_to_use_a_unique_naming_convention._".pkg.tar.zst"_is_too_long_and/or_confusing)
    -   [4.3 Pacman needs a library so other applications can easily access package information](https://wiki.archlinux.org/title/Frequently_asked_questions#Pacman_needs_a_library_so_other_applications_can_easily_access_package_information)
    -   [4.4 Pacman needs feature X!](https://wiki.archlinux.org/title/Frequently_asked_questions#Pacman_needs_feature_X!)
    -   [4.5 I just installed Package X. How do I start it?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_just_installed_Package_X._How_do_I_start_it?)
    -   [4.6 Why is there only a single version of each shared library in the official repositories?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_there_only_a_single_version_of_each_shared_library_in_the_official_repositories?)
    -   [4.7 What if I run a full system upgrade and there will be an update for a shared library, but not for the applications that depend on it?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_if_I_run_a_full_system_upgrade_and_there_will_be_an_update_for_a_shared_library,_but_not_for_the_applications_that_depend_on_it?)
    -   [4.8 Is it possible that there is a major kernel update in the repository, and that some of the driver packages have not been updated?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_it_possible_that_there_is_a_major_kernel_update_in_the_repository,_and_that_some_of_the_driver_packages_have_not_been_updated?)
    -   [4.9 What to do before upgrading?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_to_do_before_upgrading?)
    -   [4.10 A package update was released, but pacman says the system is up to date](https://wiki.archlinux.org/title/Frequently_asked_questions#A_package_update_was_released,_but_pacman_says_the_system_is_up_to_date)
    -   [4.11 Upstream project X has released a new version. How long will it take for the Arch package to update to that new version?](https://wiki.archlinux.org/title/Frequently_asked_questions#Upstream_project_X_has_released_a_new_version._How_long_will_it_take_for_the_Arch_package_to_update_to_that_new_version?)
    -   [4.12 If I need an older version of an installed library, can I just symlink to the newer version?](https://wiki.archlinux.org/title/Frequently_asked_questions#If_I_need_an_older_version_of_an_installed_library,_can_I_just_symlink_to_the_newer_version?)
-   [5 64-bit](https://wiki.archlinux.org/title/Frequently_asked_questions#64-bit)
    -   [5.1 How do I determine if my processor is x86_64 compatible?](https://wiki.archlinux.org/title/Frequently_asked_questions#How_do_I_determine_if_my_processor_is_x86_64_compatible?)
    -   [5.2 Why 64-bit?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_64-bit?)
{{< /admonition >}}

## Why BTRFS?

You might be familiar with [computer storage formats](https://en.wikipedia.org/wiki/Journaling_file_system) like ntfs, fat32 or exfat. BTRFS (better F S ) is just like that with copy-on-write principal. 

### Snapshots
As Arch Linux is a rolling model, often called bleeding edge, system will be updated a lot and a lot of things can break or repair on each update.

With btrfs you can take snapshots within seconds and it'll use less resource due to it's copy-on-write principal. And what's more you can also recover to a previous snap within a few seconds (just a simple restart),

### Boot from snapshots
And the most interesting thing is that you can add your btrfs snapshot entry to GRUB bootloader. You can use pacman hook to trigger snapshot backup before any system update and an another script to add those backup as GRUB entry.

So if something goes wrong, you can go to previous condition right from your bootloader! I'll show the way to achieve this on the [next part](/archlinux-post-install/) (post installation).

### Compression
BTRFS can compress your data as you write to save storage and it'll be helpful on the long road. Also there are some cons. [Read more here](https://itsfoss.com/btrfs/).

{{< admonition tip >}}
If you want to learn more about BTRFS then maybe a search through the web or, our favourite arch wiki is here,
- [Btrfs - ArchWiki](https://wiki.archlinux.org/title/Btrfs) 
{{< /admonition >}}

## Prerequisite

To install Arch Linux, indeed the best way to learn is Arch Wiki. But, the official guide will be little tough to understand to follow especially if you want to install on a btrfs file system or maybe a different kernel. This is why I won't be explaining everything in details and my guide is specifically for **intermediate users**.

{{< admonition danger >}}

If your intention is blindly copy paste commands from this guide or Arch wiki without understanding anything, things may not work the way you want. So I highly recommend you to install any other distro. You can try,
- [Manjaro Linux](https://manjaro.org/) - for complete newbies to learn things around and recommended for stability. 
- [EndeavourOS](https://endeavouros.com/) - it's more like graphical arch installer and highly recommended!

And keep these things in mind,
1. Avoid blindly following online tutorials and instructions. 
2. Avoid installing unnecessary packages. 
3. Avoid assuming that commands will work without understanding what they do. 
4. Avoid partitioning without understanding the implications. 
5. Avoid using the root user for regular activities. 
6. Avoid using AUR packages without understanding the risks. 
7. Avoid using unsupported or experimental software. 
8. Avoid using the default kernel if it doesn’t provide the features you need. 
9. Avoid assuming that the installation will be successful without testing. 
10. Avoid reinstalling the system without backing up your data first.

{{< /admonition >}}

## Pre-Installation

### ISO
You can grab it from [official download page](https://archlinux.org/download/). To achieve better download speed you can try a local mirror. Scroll down a bit in the [download](https://archlinux.org/download/) page. 

{{< admonition example "Example" false >}}
For example, my country is Bangladesh and I've a mirror available. I can achieve better broadband speed from this mirror!
- [XeonBD mirror](http://mirror.xeonbd.com/archlinux/iso/2022.12.01/)

It's always recommended to select the latest version. File name is like,
- *archlinux-2022.12.01-x86_64.iso*
{{< /admonition >}}

### Installation medium
You can use a [USB flash drive](https://wiki.archlinux.org/title/USB_flash_installation_medium "USB flash installation medium") or, an [optical disc](https://wiki.archlinux.org/title/Optical_disc_drive#Burning "Optical disc drive") or a network with [PXE](https://wiki.archlinux.org/title/PXE "PXE") for installation. Now USB drives are more better choice and I'll recommend you to try [ventoy](https://www.ventoy.net/en/index.html) available for almost every desktop platform. Take a backup of your drives data first and then launch **ventoy**. You can install **ventoy** on a drive, and later just copy the ISO to your drive. Specialty of **ventoy** is that you can put multiple ISO to make a multi-boot bootable USB and what's more, you can also store data (anything) on that USB. 

**[OPTIONAL]** You can also verify your ISO. Try this guide for that purpose,
-   [Verify signature](https://wiki.archlinux.org/title/Installation_guide#Verify_signature)

### Booting into live ISO
First, go to bios/ uefi setting. Different motherboard has different keybindings. You can search through web to learn more. Finally you have to point your first boot to the bootable USB or disk.

Extended guide in Arch Wiki,
-   [Acquire an installation image](https://wiki.archlinux.org/title/Installation_guide#Acquire_an_installation_image)
-   [repare an installation medium](https://wiki.archlinux.org/title/Installation_guide#Prepare_an_installation_medium)
-   [Boot the live environment](https://wiki.archlinux.org/title/Installation_guide#Boot_the_live_environment)

## Preparation

As for preparation, we'll make sure we have an active internet connection and set our keyboard's layout and time zone **[optional]**. I'll install minimal KDE plasma desktop and I can manage my time zone and keyboard's layout later using GUI. If you're using a differnet layout than English, you may want to check,
- [Set the console keyboard layout](https://wiki.archlinux.org/title/Installation_guide#Set_the_console_keyboard_layout)
- [Update the system clock](https://wiki.archlinux.org/title/Installation_guide#Update_the_system_clock) 

### Internet
If you're using **Ethernet cable**, internet connection should work out of the box. As for WiFi users, connect using [iwctl](https://wiki.archlinux.org/title/Iwctl "Iwctl"). And for mobile broadband users, try with the [mmcli](https://wiki.archlinux.org/title/Mmcli "Mmcli") utility.

{{< admonition bug "Troubleshooting" false >}}
For wireless and WWAN, make sure the card is not blocked with [rfkill](https://wiki.archlinux.org/title/Rfkill)
{{< /admonition >}}

Now, test you connection with ping,
```bash
ping 1.1.1.1
```

> Tip: **Ctrl + c** to stop a process

**Summery**,
| utility | achievement           |
| ------- | --------------------- |
| iwctl   | WiFi                  |
| mmcli   | mobile broadband      |
| ping    | check/ verify network | 

### Remote Installation (SSH)
If you want to let your friend install Arch on your PC, he can easily do it securely if both if your'e under the same local network,

Start SSH
```bash
systemctl start sshd.service
```
Set a password for root,
```bash
passwd
```
Find the IP Address

```bash
ip address
```

From your other computer, connect via SSH (You'll be prompted for the root password you just set)

```bash
ssh "root@<IP-OF-THE-FIRST-PC>
```

### Remote Installation (Internet)
But if your friend is on the [other part](/archlinux-post-install/) of the planet or not on the same network, you can use internet protocol for this.

First, sync your packages and install `tmate`,
```bash
pacman -Sy tmate
```
And, run, `tmate` and give your friend the access key!


> If you get any error, first sync with, 
> `pacman -Sy` 
> 
> and then install archlinux-keyring with, 
> `pacman -S archlinux-keyring`
> 
> later you can update archinstall,
> `pacman -S tmate`

## ArchInstall
Since [2021-04-01](https://archlinux.org/news/installation-medium-with-installer/), Arch has a guided installer [again](https://wiki.archlinux.org/title/Arch_Linux#Arch_Install_Scripts). See [archinstall](https://wiki.archlinux.org/title/Archinstall "Archinstall") for details. You can easily install Arch with the help of this script and avoid the rest of this post but if you want to extend your possibilities and configure everything with your own hand then I'll recommend the manual way.

For easily install, first get the latest package,
```bash
pacman -Sy archinstall
```
Then run,
```bash
archinstall
```

> If you get any error, first sync with, 
> `pacman -Sy` 
> 
> and then install archlinux-keyring with, 
> `pacman -S archlinux-keyring`
> 
> later you can update archinstall,
> `pacman -S archinstall`

{{< admonition tip >}}
If you're going for `archinstall`, then I would highly recommend you to install  [EndeavourOS](https://endeavouros.com/). And if you want to install arch to show up, then while installing **endeavouros** select the online method and from the package choice list deselect endevouros corresponding packages and cofigs! Then it'll install pure arch! Besides you'll find arch GUI installers in the sourceforge.
{{< /admonition >}}

## Partitioning

You can list you drives along with partitions using `lsblk` or `fdisk -l`. You may find something like, sda, sdb, etc. Here sda and sdb are two different drive/ disk. You'll also notice their partitions (if they exist). If you need to change a partition table or create or remove or resize partitions there are several tools. I'll recommend to use `cfdisk`. And to check disks and partitions size, try `df -H`.

**Summery**,
| command  | achievement                                    |
| -------- | ---------------------------------------------- |
| lsblk    | list drives along with existing partitions     |
| fdisk -l | same as above with more information            |
| df -H    | list partitions size                           |
| cfdisk   | manage partitons                               |
| parted   | third party to manage partitions (Gparted CLI) | 

### Layouts

It's recommended to get a basic concepts of disk partitions at first. Try the following post for understanding,
- [Partitioning - ArchWiki](https://wiki.archlinux.org/title/Partitioning) 

#### Checking UEFI/ BIOS
To verify the boot mode, list the [efivars](https://wiki.archlinux.org/title/Efivars "Efivars") directory:

```bash
ls /sys/firmware/efi/efivars
```

If the command shows the directory without error, then the system is booted in UEFI mode. If the directory does not exist, the system may be booted in [BIOS](https://en.wikipedia.org/wiki/BIOS "wikipedia:BIOS") (or [CSM](https://en.wikipedia.org/wiki/Compatibility_Support_Module "wikipedia:Compatibility Support Module")) mode. If the system did not boot in the mode you desired, refer to your motherboard's manual.

#### BIOS with MBR
Check this link for an example layout,
- [Partitioning - Legacy BIOS - ArchWiki](https://wiki.archlinux.org/title/Partitioning#BIOS/MBR_layout_example)
For installation instruction on BIOS, please check this article,
- [Arch Linux Installation Process for a Legacy/BIOS/MBR System #arch-linux · GitHub](https://gist.github.com/jaymutuku/cb8d0f9734a99c19c2503d8439f79e71)
Also YouTube has quite a few full tutorials available!

#### UEFI
Most of the modern system supports UEFI (even BIOS can have it! Please check your BIOS first) and so I'll continue my guide in UEFI only. You can go with the layout from Arch Wiki,
- [Partitioning - UEFI - ArchWiki](https://wiki.archlinux.org/title/Partitioning#UEFI/GPT_layout_example)

### Our layout
I'll be using 4 partition. A separate home partition. It'll allow me to keep the home partition even if I reinstall or change distro.

> **Fun fact** 
> 
> Once I downloaded the same file (using firefox) in 3 differnent Linux distro (like, 10% here, 70% there and rest in another distro). It was possible because of same home partition. But things may go ugly if you install a distro with different desktop manager, such as, plasma or gnome or, a distro with different package (like firefox 89 and firefox 108) 

**Layout,** (let our disk be **sda**)
| Mount point | partition | suggested size        | partiton type       |
| ----------- | --------- | --------------------- | ------------------- |
| /boot/efi   | sda1      | At least 300 MiB      | EFI system partiton |
| /           | sda2      | More than 10 GiB      | Linux x86-64        |
| /home       | sda3      | More than 3 GiB       | Linux x86-64        |
| [SWAP]      | sda4      | Twice the size of RAM | Linux swap          |
|             | sda5      |                       | Windows NTFS        | 
> We have an extra partition, right? We'll think about it later! So whatever we do won't effect this one. Think it as a data partiton.

{{< admonition question "F.A.Q.'s" true >}}

Why I arranged in this way?
- Well, it really doesn't matter. You can arrange in whatever way you want. I put swap at the end because in future it can allow me to resize home and swap! Some upstream suggest to put it at the beginning if you're using HDD as this part has little more read/ write rate.

Why swap?
- [Read here](https://wiki.archlinux.org/title/Swap) . You don't have to use swap partition if you want. In fact there is `systemd-swap` and `zram` concept. So feel free to avoid if you know what you're doing!

Why swap is twice the size of RAM?
- It'll help you if you hibernate your system. Most probably, you may never need to use more than 8 GiB for swap! If you don't need hibernate then equal the size of RAM is more than enough.

I have a large amount of RAM, can I avoid swap?
- Sure! In fact you should. Besides even if you've 1 GB ram you can avoid swap. Swap can be also created later as a swapfile!

Why swap partiton?
- Well, if you dual boot linux, won't it be more easy to share the same space instead of using  two separate swapfile?

{{< /admonition >}}

## Formatting partitions
First of all, if you are coming from an another distro and want to keep the **same home** partition along with users, then **avoid formatting** home partition. 

For home partition (`/home`),
```bash
mkfs.ext4 /dev/sda3
```

And you don't need to format `/boot/efi` either! In fact it can **destroy** other boot-loaders if you're trying to dual boot.

For `/boot/efi`,
```bash
mkfs.fat -F 32 /dev/sda1
```
 
 For root partition (`/`),
 ```bash
mkfs.btrfs /dev/sda2
```
 
 And finally, if you've created `swap` then initialize it by,
 ```bash
 mkswap /dev/sda4
```

## Mounting partitions

#### btrfs root
We need to mount our created partitions into our linux hierarchy. **First** we need to mount sda3 (root) into /mnt.

{{< admonition tip >}}
If your root partition is **exfat** then simply try, `mount /dev/_root_partition_ /mnt` and avoid this section.
{{< /admonition >}}

We create **subvolumes** to better organize our data and to **exclude** them from btrfs snapshots.

-   @ – This is the main root subvolume /.
-   @log – Contains logs, temp. files, caches, games, etc.
-   @pkg – Contains all the pacman packages
-   @var - Contains logs, temp. files, caches, games, etc.
-   @opt - Contains third party products
-   @tmp – Contains certain temporory files and caches
-   @srv - This directory contains site-specific data that is served by this system.

{{< admonition question "F.A.Q.'s" true >}}
If I don't use separate home partiton?
-   @home – Then you have to create this subvolume!
{{< /admonition >}}

Let's mount first,
```bash
mount /dev/sda2 /mnt
```

Then, create required subvolumes,
```bash
btrfs su cr /mnt/@

btrfs su cr /mnt/@root

btrfs su cr /mnt/@srv

btrfs su cr /mnt/@log

btrfs su cr /mnt/@cache

btrfs su cr /mnt/@tmp
```

Now we see all the sub-volumes we created by using,
```bash
btrfs su li /mnt
```

| Command | Meaning   |
| ------- | --------- |
| su      | subvolume |
| cr      | create    |
| li      | list      |

Let us unmount `/mnt` and remount all sub volumes.

```bash
cd /

umount /mnt
```

Then, mount root with,
```bash
mount -o defaults,noatime,compress=zstd,commit=120,subvol=@ /dev/sda2 /mnt
```

And create directory for other subvolumes,
```bash
mkdir  /mnt/root

mkdir  /mnt/srv

mkdir -p /mnt/var/log

mkdir -p /mnt/var/cache/

mkdir /mnt/tmp
```

>Or, you can do with a one line,
>```bash
>  mkdir -p /mnt/{root,srv,var/log,var/cache,tmp}
>```

Then, you can check your work with,
```bash
lsblk
```

Then we mount the sub volumes.
```bash
mount -o defaults,noatime,compress=zstd,commit=120,subvol=@root /dev/sda2 /mnt/root

mount -o defaults,noatime,compress=zstd,commit=120,subvol=@tmp /dev/sda2 /mnt/tmp

mount -o defaults,noatime,compress=zstd,commit=120,subvol=@srv /dev/sda2 /mnt/srv

mount -o defaults,noatime,compress=zstd,commit=120,subvol=@log /dev/sda2 /mnt/var/log

mount -o defaults,noatime,compress=zstd,commit=120,subvol=@cache /dev/sda2 /mnt/var/cache
```

{{< admonition info "Btrfs options meaning," >}}

| Option   | Meaning                                                                                          |
| -------- | ------------------------------------------------------------------------------------------------ |
| noatime  | No access time. Improves system performace by not writing time when the file was accessed        |
| commit   | Periodic interval (in sec) in which data is synchronized to permanent storage.                   |
| compress | Choosing the algorithm for compress. I have set zstd as it has good compression level and speed. |
| subvol   | Choosing the subvol to mount.                                                                    | 

{{< /admonition >}}

{{< admonition info "Other guides" false >}}
You can also look at these guides if things go wrong,
YouTube,
{{< youtube Kc-ngqE84tQ  >}}
or, blog posts,
- [Installing Arch Linux with a BTRFS filesystem | ArcoLinuxD](https://www.arcolinuxd.com/installing-arch-linux-with-a-btrfs-filesystem/)
- [Arch Linux with BTRFS Installation (Base) | Tech it Out](https://www.nishantnadkarni.tech/posts/arch_installation/#step-6-partitioning-your-drive)
{{< /admonition >}}

### EFI 
Create a `mnt/boot/efi` directory,
```bash
mkdir -p /mnt/boot/efi
```
And then mount,
```bash
mount /dev/sda1 /mnt/boot/efi
```

### Home
And also one directory for `/home`,
```bash
mount --mkdir /dev/sda3 /mnt/home
```

### Swap On
And if you've created a swap partition, enable it using,
```bash
swapon /dev/sda4
```

> Now we also have a data partition with ntfs file system and we can mount it to `/mnt/any-name`, but I'll do it later. (GUI available)

## Selecting mirror
By default in the live boot, arch will generate 20 mirrors in your **mirrorlist** file, sorted by download speed. But you can achieve better internet speed by using your local mirror or by using reflector.

### Reflector
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

### Manually
We can use a text editor to edit the **mirrorlist** and set our desired mirrors also. To do that, you can use nano or vim text editor or install any CLI-based text editor if you need. And there's an online arch mirror list generator,
- [Arch Linux - Pacman Mirrorlist Generator](https://archlinux.org/mirrorlist/)

Simply edit the `mirrorlist` file, like,
```bash
nano /etc/pacman.d/mirrorlist
```

## archlinux-keyring
Without installing this package, you may face `Failed to commit transaction (invalid or corrupted package)` or similar. To avoid, first sync with, 
```bash
pacman -Sy
```

and then install **archlinux-keyring** with, 
```bash
pacman -S archlinux-keyring
```

## Essential packages
Use the [pacstrap(8)](https://man.archlinux.org/man/pacstrap.8) script to install the [base](https://archlinux.org/packages/?name=base) package and firmware for common hardware,
```bash
pacstrap -K /mnt base base-devel linux-firmware
```

And, then you can also install the `linux` kernel like, but I'll be installing `linux-zen` kernel. It's your choice. For installing `linux-zen` my command will be,
```bash
pacstrap  /mnt linux-zen
```

> For `vanilla-linux` kernel, try,
> ```bash
> pacstrap  /mnt linux
> ```

## System configuration

### fstab
When you start your system it'll help Arch to determine mount points which [we set manually](#mounting-partitions). To generate it, use,
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

### entering chroot
Now change root into our system!
```bash
arch-chroot /mnt
```

## chroot
This section covers some suggested tasks that you may want to after [entering chroot](#entering-chroot).

### root password
To set `root password` try,
```bash
passwd
```

> We'll need this password later, so try not to forget it!

### network

#### network manager
Install a network manager with,
```bash
pacman -S networkmanager
```

and then, enable it with,
```bash
systemctl enable NetworkManager.service
```

#### host-name
use a text-editor to set a host name,
```bash
nano /etc/hostname
```
In the text file, put any name and save it!

#### hosts
**[OPTIONAL]** I'll be editing my hosts later. Because with hosts you can even do ad-blocking, malicious site blocking or adult site blocking. I'll add it in the [post installation part](/archlinux-post-install/). For now you can safely avoid this part.

But if you want to allow resolving the local host-name, edit,
```bash
nano /etc/hosts
```
and append these lines (recommended by Arch Wiki),
```bash
127.0.0.1        localhost
::1              localhost
127.0.1.1        _myhostname_
```

> replace **_myhostname_** with your actual host-name, you set before!

### Microcode
To acquire updated microcode, depending on the processor, [install](https://wiki.archlinux.org/title/Install "Install") one of the following packages,

-   [amd-ucode](https://archlinux.org/packages/?name=amd-ucode) for AMD processors,
-   [intel-ucode](https://archlinux.org/packages/?name=intel-ucode) for Intel processors.

for `intel`, my command will be,
```bash
pacman -S intel-ucode
```

> Do this before the [next step](#bootloader) to make sure it's starting with bootloader.

### Bootloader
This step is different for UEFI and non-UEFI systems. For EFI, inside the `arch-chroot`, 
install `grub` and `efibootmgr`,
```bash
pacman -S grub efibootmgr
```

and then install grub like,
```bash
grub-install --target=x86_64-efi --bootloader-id=GRUB --efi-directory=/boot/efi
```

Then generate config with,
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

### Localization
edit your `locale.gen` file, like,
```bash
nano /etc/locale.gen
```

Then search for your desired locale, write it down (take note) ,and un-comment it (remove the `#` from the beginning of a line). In `nano` text editor you can use `ctrl + w` to search. Then press, `ctrl + o` to save, followed by an `enter` and then `ctrl + x` to exit.

Later, generate your config by running,
```bash
locale-gen
```

And, add it to the config file, (remember I told you to note that down? You have to use the first part),
```bash
nano /etc/locale.conf
```

Here's a sample (I'm using US English)
```bash
LANG=en_US.UTF-8
```

### Additional steps
Now you can do some additional configuration if you want, like setting up timezone, initial services etc. I will be installing KDE plasma and I can do all of those from plasma's setting so I'll avoid those. But if you want you can do it. Here are some references,
-   [Time zone](https://wiki.archlinux.org/title/Installation_guide#Time_zone)
-   [Initramfs](https://wiki.archlinux.org/title/Installation_guide#Initramfs) **[OPTIONAL]**

## Wrapping up

### Reboot
After configuring from inside of `arch-chroot` you can leave `arch-chroot` by using,
```bash
exit
```
And, believe it or not, we've successfully installed Arch. Now feel free to reboot with,
```bash
reboot
```

### What to expect?
If you reboot/ restart then you will first notice a GRUB bootloader which will wait 5 seconds for you, or you can just select your kernel and hit enter. Later you'll be greeted with a CLI login prompt where you can login as `root` (username = 'root')! Remember the password [from this part](#root-password)? Use it to login.

Why that GRUB and black and white terminal?
- No need to worry, we'll both hide that GRUB 5 seconds and black and white login prompt in the next part.

Stucked in GRUB?
- `arch-chroot` into your root and make sure, a kernel with base is installed and run `grub-mkconfig` again.
- Unmount and reboot

### Forgot root password?
- Boot into live ISO
- Mount the root partiton
- `arch-chroot` into root
- Use the `passwd` command to set the new password (you will not be prompted for an old one).
- Unmount and reboot

### References
- [Installation guide - ArchWiki](https://wiki.archlinux.org/title/Installation_guide#Configure_the_system)
- [How to Install Arch Linux in 2022 | It'sFOSS](https://itsfoss.com/install-arch-linux/) 
- [Arch Linux Installation Guide For Developers | LunaTrace](https://www.lunasec.io/docs/blog/arch-linux-installation-guide/#enabling-ssh)
- [Installing Arch Linux with a BTRFS filesystem | ArcoLinuxD](https://www.arcolinuxd.com/installing-arch-linux-with-a-btrfs-filesystem/)
- [Arch Linux with BTRFS Installation (Base) | Tech it Out](https://www.nishantnadkarni.tech/posts/arch_installation/#step-6-partitioning-your-drive) 

### What's next?
Now you can install any desktop environment or any window manager with your favorite softwares! If you want I can pick you up right from where you're now with my next post,
- [Arch Linux Post Install with minimal plasma and more](/archlinux-post-install/)