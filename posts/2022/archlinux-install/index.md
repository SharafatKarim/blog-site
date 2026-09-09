---
title: Archlinux minimal Install with btrfs
date: 2022-12-19T15:25:33+06:00
lastmod: 2026-09-09T19:05:57+06:00
draft: false
author: Sharafat Karim
authorLink: https://sharafat.pages.dev/about/
description: A complete guide to install Arch Linux with btrfs, linux zen kernel and minimal kde plasma with advanced snapshot support!
license: <a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>
images: 
resources:
  - name: featured-image
    src: featured.jpg
tags:
  - linux
  - os
  - tutorial
  - arch
  - kde
  - btrfs
  - plasma
categories:
  - tutorial
summary: A complete guide to install Arch Linux with btrfs, linux zen kernel and minimal kde plasma with advanced snapshot support! (part one)
featuredImage: featured-image
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
mapbox: 
share:
  enable: true
comment:
  enable: true
library:
  css: 
  js: 
seo:
  images: []
---

# Arch Linux Installation Guide

## Introduction

If you don't know about Arch Linux, and willing to learn, then check this post,

- [Arch Linux](https://wiki.archlinux.org/title/Arch_Linux)

In this guide I'll be installing Arch Linux with BTRFS. And [in a separate article](/archlinux-post-install/) I'll show you the way to a minimal KDE plasma desktop along with some extended possibilities. If you're reading this I can assume you are already familiar with [archwiki](https://wiki.archlinux.org/) - a great place to learn about Arch Linux!

{{< admonition tip >}}
This post will be long and may be hard to navigate without TOC (Table of Contents). So please use table of contents. On desktop it's placed on the right side and mobile device users can access it from the very top of the post.
{{< /admonition >}}

## Why Arch?

If you don't have much idea about different distros, maybe you can read this [article](https://wiki.archlinux.org/title/Arch_compared_to_other_distributions). Also you'll find a lot of guys in YouTube for this purpose (to explain you why you need arch). If you've much free time to tinker with your system and you are in need of a full time job with no salary, welcome to the arena! I'll highly recommend you to try Arch Linux.

{{< admonition question "F.A.Q.'s" false >}}
From [ArchWiki](https://wiki.archlinux.org/title/Frequently_asked_questions)

- [1 General](https://wiki.archlinux.org/title/Frequently_asked_questions#General)
  - [1.1 What is Arch Linux?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_is_Arch_Linux?)
  - [1.2 Why would I not want to use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_would_I_not_want_to_use_Arch?)
  - [1.3 Why would I want to use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_would_I_want_to_use_Arch?)
  - [1.4 What architectures does Arch support?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_architectures_does_Arch_support?)
  - [1.5 Does Arch follow the Linux Foundation's Filesystem Hierarchy Standard (FHS)?](https://wiki.archlinux.org/title/Frequently_asked_questions#Does_Arch_follow_the_Linux_Foundation's_Filesystem_Hierarchy_Standard_(FHS)?)
  - [1.6 I am a complete GNU/Linux beginner. Should I use Arch?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_am_a_complete_GNU/Linux_beginner._Should_I_use_Arch?)
  - [1.7 Is Arch designed to be used as a server? A desktop? A workstation?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_Arch_designed_to_be_used_as_a_server?_A_desktop?_A_workstation?)
  - [1.8 I really like Arch, except the development team needs to implement feature X](https://wiki.archlinux.org/title/Frequently_asked_questions#I_really_like_Arch,_except_the_development_team_needs_to_implement_feature_X)
  - [1.9 When will the new release be made available?](https://wiki.archlinux.org/title/Frequently_asked_questions#When_will_the_new_release_be_made_available?)
  - [1.10 Is Arch Linux a stable distribution? Will I get frequent breakage?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_Arch_Linux_a_stable_distribution?_Will_I_get_frequent_breakage?)
  - [1.11 Arch needs more press (i.e. advertisement)](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_more_press_(i.e._advertisement))
  - [1.12 Arch needs more developers](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_more_developers)
- [2 Installation](https://wiki.archlinux.org/title/Frequently_asked_questions#Installation)
  - [2.1 Arch needs an installer. Maybe a GUI installer?](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_needs_an_installer._Maybe_a_GUI_installer?)
  - [2.2 I installed Arch, and now I am at a shell! What now?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_installed_Arch,_and_now_I_am_at_a_shell!_What_now?)
  - [2.3 Which desktop environment or window manager should I use?](https://wiki.archlinux.org/title/Frequently_asked_questions#Which_desktop_environment_or_window_manager_should_I_use?)
  - [2.4 What makes Arch unique amongst other "minimal" distributions?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_makes_Arch_unique_amongst_other_"minimal"_distributions?)
- [3 System maintenance](https://wiki.archlinux.org/title/Frequently_asked_questions#System_maintenance)
  - [3.1 Why is my internet so slow compared to other operating systems?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_my_internet_so_slow_compared_to_other_operating_systems?)
  - [3.2 Why is Arch using all my RAM?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_Arch_using_all_my_RAM?)
  - [3.3 Where did all my free space go?](https://wiki.archlinux.org/title/Frequently_asked_questions#Where_did_all_my_free_space_go?)
- [4 Package management](https://wiki.archlinux.org/title/Frequently_asked_questions#Package_management)
  - [4.1 I have found an error with package X. What should I do?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_have_found_an_error_with_package_X._What_should_I_do?)
  - [4.2 Arch packages need to use a unique naming convention. ".pkg.tar.zst" is too long and/or confusing](https://wiki.archlinux.org/title/Frequently_asked_questions#Arch_packages_need_to_use_a_unique_naming_convention._".pkg.tar.zst"_is_too_long_and/or_confusing)
  - [4.3 Pacman needs a library so other applications can easily access package information](https://wiki.archlinux.org/title/Frequently_asked_questions#Pacman_needs_a_library_so_other_applications_can_easily_access_package_information)
  - [4.4 Pacman needs feature X!](https://wiki.archlinux.org/title/Frequently_asked_questions#Pacman_needs_feature_X!)
  - [4.5 I just installed Package X. How do I start it?](https://wiki.archlinux.org/title/Frequently_asked_questions#I_just_installed_Package_X._How_do_I_start_it?)
  - [4.6 Why is there only a single version of each shared library in the official repositories?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_is_there_only_a_single_version_of_each_shared_library_in_the_official_repositories?)
  - [4.7 What if I run a full system upgrade and there will be an update for a shared library, but not for the applications that depend on it?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_if_I_run_a_full_system_upgrade_and_there_will_be_an_update_for_a_shared_library,_but_not_for_the_applications_that_depend_on_it?)
  - [4.8 Is it possible that there is a major kernel update in the repository, and that some of the driver packages have not been updated?](https://wiki.archlinux.org/title/Frequently_asked_questions#Is_it_possible_that_there_is_a_major_kernel_update_in_the_repository,_and_that_some_of_the_driver_packages_have_not_been_updated?)
  - [4.9 What to do before upgrading?](https://wiki.archlinux.org/title/Frequently_asked_questions#What_to_do_before_upgrading?)
  - [4.10 A package update was released, but pacman says the system is up to date](https://wiki.archlinux.org/title/Frequently_asked_questions#A_package_update_was_released,_but_pacman_says_the_system_is_up_to_date)
  - [4.11 Upstream project X has released a new version. How long will it take for the Arch package to update to that new version?](https://wiki.archlinux.org/title/Frequently_asked_questions#Upstream_project_X_has_released_a_new_version._How_long_will_it_take_for_the_Arch_package_to_update_to_that_new_version?)
  - [4.12 If I need an older version of an installed library, can I just symlink to the newer version?](https://wiki.archlinux.org/title/Frequently_asked_questions#If_I_need_an_older_version_of_an_installed_library,_can_I_just_symlink_to_the_newer_version?)
- [5 64-bit](https://wiki.archlinux.org/title/Frequently_asked_questions#64-bit)
  - [5.1 How do I determine if my processor is x86_64 compatible?](https://wiki.archlinux.org/title/Frequently_asked_questions#How_do_I_determine_if_my_processor_is_x86_64_compatible?)
  - [5.2 Why 64-bit?](https://wiki.archlinux.org/title/Frequently_asked_questions#Why_64-bit?)
{{< /admonition >}}

## Why BTRFS?

You might be familiar with [computer storage formats](https://en.wikipedia.org/wiki/Journaling_file_system) like ntfs, fat32 or exfat. Btrfs (B-tree Filesystem, nicknamed Butter FS) is a modern filesystem built around the copy-on-write principle.

### Snapshots

As Arch Linux is a rolling model, often called bleeding edge, system will be updated a lot and a lot of things can break or repair on each update.

With btrfs you can take snapshots within seconds and it'll use less resource due to it's copy-on-write principle. And what's more you can also recover to a previous snap within a few seconds (just a simple restart),

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

{{< admonition tip "And," false >}}
If you want, you can also try third party builds of ArchLinux. Check the following link,

- [Archboot - Additional Arch Linux ISOs And UKIs](https://archboot.com/)
{{< /admonition >}}

### Installation medium

You can use a [USB flash drive](https://wiki.archlinux.org/title/USB_flash_installation_medium "USB flash installation medium") or, an [optical disc](https://wiki.archlinux.org/title/Optical_disc_drive#Burning "Optical disc drive") or a network with [PXE](https://wiki.archlinux.org/title/PXE "PXE") for installation. Now USB drives are more better choice and I'll recommend you to try [ventoy](https://www.ventoy.net/en/index.html) available for almost every desktop platform. Take a backup of your drives data first and then launch **ventoy**. You can install **ventoy** on a drive, and later just copy the ISO to your drive. Specialty of **ventoy** is that you can put multiple ISO to make a multi-boot bootable USB and what's more, you can also store data (anything) on that USB.

**[OPTIONAL]** You can also verify your ISO. Try this guide for that purpose,

- [Verify signature](https://wiki.archlinux.org/title/Installation_guide#Verify_signature)

### Booting into live ISO

First, go to bios/ uefi setting. Different motherboard has different keybindings. You can search through web to learn more. Finally you have to point your first boot to the bootable USB or disk.

Extended guide in Arch Wiki,

- [Acquire an installation image](https://wiki.archlinux.org/title/Installation_guide#Acquire_an_installation_image)
- [Prepare an installation medium](https://wiki.archlinux.org/title/Installation_guide#Prepare_an_installation_medium)
- [Boot the live environment](https://wiki.archlinux.org/title/Installation_guide#Boot_the_live_environment)

## Preparation

As for preparation, we'll make sure we have an active internet connection and set our keyboard's layout and time zone **[optional]**. I'll install minimal KDE plasma desktop and I can manage my time zone and keyboard's layout later using GUI. If you're using a different layout than English, you may want to check,

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

**Summary**,

| utility | achievement           |
| ------- | --------------------- |
| iwctl   | WiFi                  |
| mmcli   | mobile broadband      |
| ping    | check/ verify network |

### Remote Installation (SSH)

If you want to let your friend install Arch on your PC, he can easily do it securely if both if your're under the same local network,

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
ssh root@<IP-OF-THE-FIRST-PC>
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

**Summary**,

| command  | achievement                                    |
| -------- | ---------------------------------------------- |
| lsblk    | list drives along with existing partitions     |
| fdisk -l | same as above with more information            |
| df -H    | list partitions size                           |
| cfdisk   | manage partitions                              |
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

Instead of creating a rigid, separate `ext4` partition for `/home` and a dedicated swap partition, we will use a clean 2-partition scheme with a unified Btrfs storage pool. With Btrfs, subvolumes (such as `@` for root and `@home` for user directories) dynamically share the same free space across the pool. There's no need to guess ahead of time how many gigabytes `/` or `/home` will need—both grow and shrink dynamically as files are created and removed!

For swap, we will set up a flexible Btrfs swapfile in the [post-installation part (part 2)](/archlinux-post-install/) rather than locking up storage in a fixed partition.

We standardize our EFI system partition mount point to `/boot` (FAT32, at least 512 MiB–1 GiB).

**Layout,** (let our disk be **sda**)

| Mount Point | Partition | Suggested Size | Partition Type | Filesystem |
| :--- | :--- | :--- | :--- | :--- |
| `/boot` | `sda1` | 512 MiB – 1 GiB | EFI system partition | FAT32 |
| Btrfs Pool | `sda2` | Remaining space | Linux filesystem | Btrfs |
| Data / Windows | `sda3` | Optional | NTFS / ExFAT | NTFS |

> We have an extra partition, right? We'll think about it later! So whatever we do won't affect this one. Think of it as a data partition.

{{< admonition question "F.A.Q.'s" true >}}

Why a unified Btrfs pool instead of separate partitions?

- Btrfs subvolumes act like self-contained filesystems inside a single partition. Since `@` and `@home` share remaining disk space dynamically, you never run into situations where your root partition runs out of space while your `/home` partition sits mostly empty.

Why no swap partition?

- Dedicated swap partitions waste disk space if you don't need them constantly. Modern Btrfs supports swapfiles cleanly, or you can use `zram-generator` (RAM compression). We will create and configure a swapfile in the [post-installation guide](/archlinux-post-install/).

{{< /admonition >}}

## Formatting partitions

For the EFI partition (`/boot`), format it as FAT32 (make sure you don't accidentally reformat an existing EFI partition if you are dual-booting with Windows!):

```bash
mkfs.fat -F 32 /dev/sda1
```

For our main Btrfs storage pool partition:

```bash
mkfs.btrfs /dev/sda2
```

{{< admonition tip >}}
After formatting, you can label your partitions for easily identifying them later. For example:

```bash
fatlabel /dev/sda1 EFI
btrfs filesystem label /dev/sda2 ARCH
```

{{< /admonition >}}

## Mounting partitions & Btrfs Subvolumes

### Btrfs Subvolume Layout

We create **subvolumes** to organize our data, enable instant snapshots, and cleanly separate dynamic or cache directories from system rollbacks.

We standardize on the official 5-subvolume layout used by `archinstall`:

- `@` -> `/` (Root filesystem)
- `@home` -> `/home` (User personal files & configs)
- `@pkg` -> `/var/cache/pacman/pkg` (Pacman package download cache)
- `@log` -> `/var/log` (System and journal logs)
- `@snapshots` -> `/.snapshots` (Btrfs root snapshot store)

{{< admonition danger "Do NOT isolate /var or /var/lib/pacman!" >}}
Never create a generic `@var` subvolume or separate `/var/lib/pacman` into its own subvolume! The package database in `/var/lib/pacman` must stay inside the root `@` subvolume. If `/var/lib/pacman` is isolated, rolling back your root filesystem snapshot will cause the installed binaries on `/` and the pacman package database to become desynchronized, leading to broken dependencies and system corruption.
{{< /admonition >}}

### Creating Subvolumes

Let's mount the Btrfs partition to `/mnt` temporarily:

```bash
mount /dev/sda2 /mnt
```

Now create the 5 subvolumes:

```bash
btrfs subvolume create /mnt/@
btrfs subvolume create /mnt/@home
btrfs subvolume create /mnt/@pkg
btrfs subvolume create /mnt/@log
btrfs subvolume create /mnt/@snapshots
```

You can view all the subvolumes you created using:

```bash
btrfs subvolume list /mnt
```

Unmount `/mnt`:

```bash
umount /mnt
```

### Mounting Subvolumes & Partitions

Now we remount the root subvolume (`@`) with safe, modern mount options:

```bash
# Mount root
mount -o noatime,compress=zstd,subvol=@ /dev/sda2 /mnt
```

Create the directory mount points:

```bash
# Create mount points
mkdir -p /mnt/{boot,home,.snapshots}
mkdir -p /mnt/var/log
mkdir -p /mnt/var/cache/pacman/pkg
```

Mount the remaining subvolumes and EFI partition:

```bash
# Mount remaining subvolumes
mount -o noatime,compress=zstd,subvol=@home /dev/sda2 /mnt/home
mount -o noatime,compress=zstd,subvol=@pkg /dev/sda2 /mnt/var/cache/pacman/pkg
mount -o noatime,compress=zstd,subvol=@log /dev/sda2 /mnt/var/log
mount -o noatime,compress=zstd,subvol=@snapshots /dev/sda2 /mnt/.snapshots

# Mount EFI partition
mount /dev/sda1 /mnt/boot
```

{{< admonition info "Btrfs mount options explained:" >}}

| Option   | Meaning                                                                                          |
| -------- | ------------------------------------------------------------------------------------------------ |
| noatime  | Disables access time updates on files when read. Greatly improves I/O performance and SSD life.  |
| compress | Enables transparent compression (`zstd`). Saves significant disk space and improves read speeds.|
| subvol   | Specifies which Btrfs subvolume to mount at the target mount point.                              |

{{< /admonition >}}

## Selecting mirror

By default in the live boot, arch will generate mirrors in your **mirrorlist** file. You can achieve better download speeds by sorting fast local mirrors using reflector.

### Reflector

With reflector you can easily update your mirrorlist:

```bash
reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```

### Manually

You can also use a text editor to edit `/etc/pacman.d/mirrorlist` directly:

```bash
nano /etc/pacman.d/mirrorlist
```

## archlinux-keyring

To prevent `invalid or corrupted package` signature errors during installation, ensure the keyring is up to date:

```bash
pacman -Sy archlinux-keyring
```

## Essential packages

Use the [pacstrap(8)](https://man.archlinux.org/man/pacstrap.8) script with `-K` (to initialize an empty pacman keyring in the target system) to install the base system, kernel, development tools, Btrfs utilities, and networking:

```bash
pacstrap -K /mnt base base-devel linux-zen linux-firmware btrfs-progs nano networkmanager
```

> **Note on Kernels:** We are installing `linux-zen` for optimized desktop performance. If you prefer the standard upstream kernel or the long-term stable kernel, simply replace `linux-zen` with `linux` or `linux-lts`.

{{< admonition tip >}}
If you are using the `linux-zen` kernel, you can optionally install `linux-zen-headers` for building kernel modules (such as DKMS drivers, VirtualBox, or NVIDIA):

```bash
pacstrap /mnt linux-zen-headers
```

{{< /admonition >}}

## System configuration

### fstab

Generate the `fstab` file using UUIDs so Arch knows where to mount your Btrfs subvolumes and EFI partition on boot:

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

### entering chroot

Now change root into your new system!

```bash
arch-chroot /mnt
```

## chroot

This section covers essential configuration inside your new system.

### root password

To set the `root` password:

```bash
passwd
```

> We'll need this password to log in on first boot, so make sure to remember it!

### network

Enable NetworkManager so network services start automatically on boot:

```bash
systemctl enable NetworkManager.service
```

#### host-name

Set your system hostname:

```bash
nano /etc/hostname
```

Enter your desired machine name (e.g. `archlinux`) and save.

#### hosts

Configure `/etc/hosts`:

```bash
nano /etc/hosts
```

Append the standard local loopback entries:

```text
127.0.0.1        localhost
::1              localhost
127.0.1.1        myhostname
```

> Replace `myhostname` with the actual hostname you configured above.

### Microcode

Install processor microcode updates:

- For AMD CPUs:
  ```bash
  pacman -S amd-ucode
  ```
- For Intel CPUs:
  ```bash
  pacman -S intel-ucode
  ```

### Bootloader

Install GRUB and EFI boot manager utilities:

```bash
pacman -S grub efibootmgr
```

Install GRUB to the `/boot` EFI directory:

```bash
grub-install --target=x86_64-efi --bootloader-id=GRUB --efi-directory=/boot
```

Then generate the GRUB configuration file:

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

### Localization

Edit `/etc/locale.gen`:

```bash
nano /etc/locale.gen
```

Un-comment your locale (for instance, remove the `#` before `en_US.UTF-8 UTF-8`). Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X` in nano).

Generate the locales:

```bash
locale-gen
```

Set the system locale in `/etc/locale.conf`:

```bash
echo "LANG=en_US.UTF-8" > /etc/locale.conf
```

### Additional steps

#### Timezone & Hardware Clock

Set your local timezone and synchronize the hardware clock to prevent clock desynchronization on first boot:

```bash
ln -sf /usr/share/zoneinfo/Asia/Dhaka /etc/localtime
hwclock --systohc
```

> Substitute `Asia/Dhaka` with your region/city (see available zones in `/usr/share/zoneinfo/`).

You can also check the ArchWiki for further initramfs or console customization:

- [Initramfs](https://wiki.archlinux.org/title/Installation_guide#Initramfs) **[OPTIONAL]**

## Wrapping up

### Reboot

Leave the chroot environment:

```bash
exit
```

Unmount all partitions and reboot into your new Arch Linux system:

```bash
umount -R /mnt
reboot
```

### What to expect on first boot

After rebooting, select Arch Linux in the GRUB menu. You'll arrive at a terminal login prompt:
1. Log in as `root` using the password you set during installation.
2. For connecting to Wi-Fi via terminal, use the interactive NetworkManager TUI tool:
   ```bash
   nmtui
   ```
   Select **Activate a connection**, choose your Wi-Fi SSID, enter the password, and you're online!

> Stuck in GRUB? If you ever find yourself in the `grub-rescue` shell, see below.

### Grub rescue?

If you ever encounter the grub rescue shell (e.g. if `grub-mkconfig` was missed):

#### 1. `ls`

List all available partitions and devices:

```shell
grub rescue> ls
```

#### 2. `set`

Inspect current Grub environment variables:

```shell
grub rescue> set
```

#### 3. `set prefix`

Set the prefix pointing to your GRUB directory (since `/boot` is mounted on partition 1):

```shell
grub rescue> set prefix=(hd0,gpt1)/grub
```

#### 4. `set root`

Set the root partition to the boot partition:

```shell
grub rescue> set root=(hd0,gpt1)
```

#### 5. `insmod`

Load the normal boot module:

```shell
grub rescue> insmod normal
```

#### 6. `normal`

Launch the standard menu:

```shell
grub rescue> normal
```

#### 7. `boot`

Boot the system:

```shell
grub rescue> boot
```

### References

- [Installation guide - ArchWiki](https://wiki.archlinux.org/title/Installation_guide#Configure_the_system)
- [Btrfs - ArchWiki](https://wiki.archlinux.org/title/Btrfs)
- [How to Install Arch Linux | It'sFOSS](https://itsfoss.com/install-arch-linux/)
- [Installing Arch Linux with a BTRFS filesystem | ArcoLinuxD](https://www.arcolinuxd.com/installing-arch-linux-with-a-btrfs-filesystem/)

### What's next?

Now you can install your choice of desktop environment or window manager! Follow along in the next post for setting up minimal KDE Plasma and automated Btrfs snapshot boot support:

- [Arch Linux Post Install with minimal plasma and more](/archlinux-post-install/)
