---
title: "Archlinux Install"
date: 2022-12-19T15:25:33+06:00
lastmod: 2022-12-19T15:25:33+06:00
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

If you don't know about Arch Linux, and willing to learn, then check this post,
- [Arch Linux](https://wiki.archlinux.org/title/Arch_Linux)

In this guide I'll be installing Arch Linux with BTRFS. And in a separate article I'll show you the way to a minimal KDE plasma desktop along with some extended possibilities. If you're reading this I can assume you are already familiar with [archwiki](https://wiki.archlinux.org/) - a great place to learn about Arch Linux!

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

So if something goes wrong, you can go to previous condition right from your bootloader! I'll show the way to achieve this on the next part (post installation).

### Compression
BTRFS can compress your data as you write to save storage and it'll be helpful on the long road. Also there are some cons. [Read more here](https://itsfoss.com/btrfs/).

{{< admonition tip >}}
If you want to learn more about BTRFS then maybe a search through the web or, our favourite arch wiki is here,
- [Btrfs - ArchWiki](https://wiki.archlinux.org/title/Btrfs) 
{{< /admonition >}}

## Prerequisite

To install Arch Linux, indeed the best way to learn is Arch Wiki. But, the official guide will be little tough to understand to follow especially if you want to install on a btrfs file system or maybe a different kernel. This is why I won't be explaining everything in details and my guide is specifically for **intermediate users**.

{{< admonition danger >}}

If your intention is blindly copy paste commands from this guide or Arch wiki without understanding anything things may not work the way you want. So I highly recommend you to install any other distro. You can try,
- [Manjaro Linux](https://manjaro.org/) - complete newbies to learn things around and recommended for stability. 
- [EndeavourOS](https://endeavouros.com/) - it's more like graphical arch installer and highly recommended!

{{< /admonition >}}

## Pre-Installation

### ISO
You can grab it from [official download page](https://archlinux.org/download/). To achieve better download speed you can try a local mirror. Scroll down a bit in the [download](https://archlinux.org/download/) page. 

{{< admonition example >}}
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
As for preparation, we'll make sure we have an acti