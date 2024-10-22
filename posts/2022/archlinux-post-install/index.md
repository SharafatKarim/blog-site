---
title: "Archlinux Post Install with minimal plasma"
date: 2022-12-20T18:38:11+06:00
lastmod: 2023-01-29T18:38:11+06:00
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
summary: "A complete guide to install Arch Linux with btrfs, linux zen kernel and minimal kde plasma with advace snapshot support! (part two)"

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

This is the continuation of the Arch Linux installation's [part one](/archlinux-install/). In the [part one](/archlinux-install/), we've installed Arch with as less afford as possible. In this part we'll install from desktop environment to our GRUB setup with BTRFS snapshots integration and a lot of possibilities! In case you haven't checked [part one](/archlinux-install/) yet, it's recommended if you want to install to Arch from scratch,
- [Arch minimal installation | part one](/archlinux-install/)

## Prerequisite
If you've followed my [part one](/archlinux-install/), you are probably in a black background with white bash prompt. Feel free to login with your username, 'root' and your root account's password. Now let's check our system a bit,

### Intenet
Check your internet connection with ping,
```bash
ping 1.1.1.1
```

> Tip: **Ctrl + c** to stop a process

And it should work out of the box for Ethernet. But you have to manually setup if you are using wireless connections. If you encounter any problem, check `NetworkManager` 's status with,
```bash
systemctl status NetworkManager
```

If it's disabled, you can enable and start with, `systemctl enable` and `systemctl start` command or just rebooting your system.

> For Wi-Fi connection, you can use `nmcli`, a command line tool for network manager. For guidance, check,
>- [nmcli-examples(7) — Arch manual pages](https://man.archlinux.org/man/nmcli-examples.7.en)
> - [How to Connect to Wi-Fi Through the Linux Terminal With Nmcli](https://www.makeuseof.com/connect-to-wifi-with-nmcli/).

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


## Plasma Essential
Besides a browser, for convenience we'll install our favorite file manager and terminal utilities. And if you're going for plasma we'll also try some plasma integrations like, network manager support and kde plasmoids.

Let's let it install and let me describe what they are,
```bash
pacman -S firefox plasma-nm plasma-pa dolphin konsole kdeplasma-addons kde-gtk-config kscreen
```

And here's a short description,

| Application name | Application's description                                                                                                                                       |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| firefox          | A FOSS browser, which is favorite to a lot of linux users and you can also customize it with CSS. But of course you can also use anything else that you prefer. |
| plasma-nm        | Network manager integration with plasma. With this you can easily configure network with your plasma desktop.                                                   |
| plasma-pa        | Plasma applet for audio volume management using  PulseAudio                                                                                                     |
| dolphin          | A file manger for plasma. It's really recommended because of it's availability, user interface and a lot of features out of the box.                            |
| konsole          | A terminal app for plasma. It's highly configurable through GUI and easy to integrate with plasma.                                                              |
| kdeplasma-addons | **[OPTIONAL]** Extra addons like color picker and monitor.                                                                                                      |
| kde-gtk-config   | It'll allow you to customize gtk apps through kde's setting and recommended to install.                                                                         |
| kscreen          | It does the job behind desktop and monitor configuration setting. Without it, monitor setting can be missing from the system settings.                          |

> More `plasma-essentials` are listed on, [plasma extras section](#plasma-extras). Because plasma application needs to be installed with optional dependencies for extended features!

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

## Drivers
In linux, drivers are mostly included in the kernel. But for some proprietary drivers like Nvidia, you may need to install them manually. It's better to directly read the wiki for your use case.

- [AMD GPU](https://wiki.archlinux.org/title/AMDGPU)
- [Intel graphics](https://wiki.archlinux.org/title/Intel_graphics)
- [Nvidia](https://wiki.archlinux.org/title/NVIDIA)

> Don't have GPU? Well,  you can look for vulkan drivers!

## Packages

### Official packages
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
Once you install `chaotic-AUR` you can just use your pacman to install from chaotic AUR. To setup `chaotic AUR` you can go to it's [official website](https://aur.chaotic.cx/) and follow along. Or, make sure `wget` is installed (`sudo pacman -S --needed wget`) and run this script, it'll do the job for you(made by me). Just open terminal and run,
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

And for configuration, you can set mirror just like you did in the arch installation process ([part one](/archlinux-install/)),
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
>
> And in case you want to get the latest 20 mirrors, sorted by speed, you can also do this,
>
> ```bash
> reflector --latest 20 --sort rate --save /etc/pacman.d/mirrorlist
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

### Multilib
Multilib is a repository that contains 32-bit software for 64-bit systems. If you're using a 64-bit system then you might want to enable it. To do so, just edit the `/etc/pacman.conf` file and un-comment the lines,
```bash
[multilib]
Include = /etc/pacman.d/mirrorlist
```

### Parralel download
You can also enable parallel download in pacman. To do so, just edit the `/etc/pacman.conf` file and un-comment the line `ParallelDownloads` (removing `#` from a line),
```bash
ParallelDownloads
```

### Bit of ASCII art
And if you're a fan of ASCII art then you can enable it in pacman. To do so, just edit the `/etc/pacman.conf` file and add the line `ILoveCandy`,
```bash
ILoveCandy
```
> Where to put it? I just put it after `color` due to simillarity.

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
### Bash and zsh
By default your shell is `bash`. And you can enhance your possibilities with an another shell like `zsh` or `fish`. You can also do a lot with your `.bashrc` file. If you're looking for a nice beautiful `zsh` shell with useful plugins like, auto coloring, auto completion then I've a separate tutorial for you.
- [Zsh and antigen](/zsh-and-antigen/)

### Autostart
To autostart something, for example `fastfetch` (a `neofetch` alternative), or something funny like `cowsay` or `fortune` or `pokemon-colorscripts`, you can add it in your `~/.bashrc` or `~/.zshrc` file. Just open the file with a text editor and add the command at the end of the file. For example, for `fastfetch`,
```bash
fastfetch
```
Or, pokemon-colorscripts? It's `pokemon-colorscripts -r` to get a random pokemon 🙃.

### Libnotify
You can use `libnotify` to get notifications from your terminal. It's really useful when you're running a long process and you want to get notified when it's done. To install it, you can use pacman,
```bash
sudo pacman -S libnotify
```

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
Every time you start your system GRUB shows up and waits 5 seconds for you, right? You can actually remove it. And grub will be shown if and only if you hold `shift` key while starting. In order to achieve the fastest possible boot, instead of having GRUB wait for a timeout, it is possible for GRUB to hide the menu, unless the `Shift` key is held down during GRUB's start-up.

In order to achieve this, you should add the following line to `/etc/default/grub`:

```bash
GRUB_FORCE_HIDDEN_MENU="true"
```

Then create the file `/etc/grub.d/31_hold_shift` with,
```bash
sudo touch /etc/grub.d/31_hold_shift
```

Then, open the file with,
```bash
xdg-open /etc/grub.d/31_hold_shift
```

and paste following codes, [source](https://gist.githubusercontent.com/anonymous/8eb2019db2e278ba99be/raw/257f15100fd46aeeb8e33a7629b209d0a14b9975/gistfile1.sh)

```bash
#! /bin/sh
set -e

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"
source "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {

  if [ "x${GRUB_FORCE_HIDDEN_MENU}" = "xtrue" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

  adjust_timeout

    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
```

then make it [executable](https://wiki.archlinux.org/title/Executable "Executable"),
```bash
sudo chmod +x /etc/grub.d/31_hold_shift
```

And finally regenerate the grub configuration with,

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

**Note:** This setup uses keystatus to detect keypress event so it may not work on some machines.

### Info screen after grub
When you system starts first comes grub, and then? Something like, stating linux-zen-...., right? And do you remember when you were installing arch, while booting you say some green and white combination type progress like interface. You can actually toggle them. You have to remove a kernel parameter, called `quiet`.

To edit kernel parameters, edit `/etc/default/grub`.
And regenerate the `grub.cfg` with,
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

### Detecting other OS
Probing for other operating systems is disabled for security reasons. If still want to enable this functionality install `os-prober` and uncomment to detect and include other operating systems.

Edit `/etc/default/grub` (grub config file)
```bash
# Probing for other operating systems is disabled for security reasons. Read
# documentation on GRUB_DISABLE_OS_PROBER, if still want to enable this
# functionality install os-prober and uncomment to detect and include other
# operating systems.
GRUB_DISABLE_OS_PROBER=false
```
And finally regenerate the `grub.cfg` with,
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

## Extra partitions
Besides we'll have to mount our extra **disk partitions** as well and for that purpose we'll add NTFS support. So install `ntfs-3g`. And now you can mount ntfs partitions with `sudo mount` but it's not an idea solution. To make changes permanently you've to edit `fstab`.

### swap partition
Our swap partition should work out of the box if you've followed my [part one](/archlinux-install/) of this arch install post. To verify, run, `swapon` or, `free -h`.
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
Later launch kde partition manager, select your partition. From the right click menu, select `Edit mount point` and select the path `/mnt/data`. Finally click ok and you can reboot your session to check changes.

#### Gnome Disk Utility
The same as kde partition manager but you don't have to create the directory manually.

#### Editing fstab
You can manually set by editing, `/etc/fstab` and create an entry. To find the **UUID** try,
```bash
lsblk -f
```
To learn more, try arch wiki,
- [Fstab - Arch Wiki](https://wiki.archlinux.org/title/Fstab)

Here's a sample `/etc/fstab` for `ntfs` drive with path. Don't forget to make the directly first (/mnt/DATA) first!
```bash
/dev/nvme0n1pX                              /mnt/DATA    ntfs    nofail                                                                                                  0 0
```

## Performance
### Swap
Swap refers to the space in SSD/ HDD, which will be be used as RAM (random access), to decrease the load of your RAM. In easier words, it's necessary when you think your RAM may run out. A good gudie is available on the Arch wiki, as well as manjaro wiki.
- [Swap - Arch Wiki](https://wiki.archlinux.org/title/Swap)
- [Swap - Manjaro Wiki](https://wiki.manjaro.org/index.php?title=Swap)

{{< admonition type=note title="And," open=false >}}
Note: For Btrfs, follow the procedure described in [Btrfs#Swap](https://wiki.archlinux.org/title/Btrfs#Swap_file) in Arch Wiki.
{{< /admonition >}}

### zram and zwap
With zram generator you can easily generate zram and you can definitely try if you've a bigger ram. With zram your swap won't be used and it's definitely a bad idea to enable both zram and zswap. And `zswap` is enabled by default for most cases so you don't need to modify anything. To make sure zram is enabled, you can try,
```bash
sudo dmesg | grep swap
```

You may see somehing like, `[    0.357361] zswap: loaded using pool lz4/z3fold` if your zwap is running.

### nohang
A low ram handler. First install `nohang` from AUR or chaotic AUR. It can prevent OOM(Out of Memory). Learn more [here](https://github.com/hakavlad/nohang).
Start and enable `nohang.service` or `nohang-desktop.service` after installing,
```bash
sudo systemctl enable --now nohang-desktop.service
```

> `nohang-desktop` provides notification when you're almost out of memory.

### TRIM for SSD
If you are using SSD, you might want to turn on TRIM for your SSD health. Read more here,
- [Solid state drive - ArchWiki](https://wiki.archlinux.org/title/Solid_state_drive#Periodic_TRIM)

To verify TRIM support, run:
```shell
lsblk --discard
```

And check the values of DISC-GRAN (discard granularity) and DISC-MAX (discard max bytes) columns. Non-zero values indicate TRIM support.

For SATA SSDs only, the [hdparm](https://archlinux.org/packages/?name=hdparm) package can detect TRIM support via `hdparm -I /dev/sda | grep TRIM` as the [root user](https://wiki.archlinux.org/title/Root_user "Root user"). `hdparm` does however not support NVMe SSDs.

To enable periodic TRIM, you might like to try the following service,
```shell
systemctl enable --now fstrim.timer
```

> It's not applicable for every single SSD out there. Please execute with caution.
## Configuration

### Hosts
You can edit host files to do more than just redirecting your `localhost`. Like, ad-blocking, adult sites blocking and even more! Here's a good collection of hosts and it's regularly updated,
- [GitHub - StevenBlack/hosts: 🔒 Consolidating and extending hosts files from several well-curated sources. Optionally pick extensions for porn, social media, and other categories.](https://github.com/StevenBlack/hosts)

In the repository you'll find a file named, `host`, or just [follow this link](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts), and edit your `/etc/hosts` file and enter those texts. And then, just run,
```bash
sudo systemctl restart NetworkManager.service
```

> For convenience you can use kate text editor as it can edit system text files.

### Arch Mate
To make things more easy, I've a python script for you. With the support of that script, you can automate chaotic AUR installation, pacman packages inspection, installing essential packages etc. Here's the repository,
- [Arch Mate | A simple, lightweight, user-friendly tool for managing and configuring Arch Linux systems, written with python.](https://github.com/SharafatKarim/archmate)

> If you know python and want to contribute, feel free to send merge request or, contact with me!

## Essential packages

### Plasma extras
- As for your convenience you can try some powerful applications from KDE plasma! First of all, you can try `plasma-firewall` alongside a back-end (`ufw` or `firewalld`).

- Then to manage archives, you can try `ark`. It's pretty much strong. But you may also have to install some optional dependencies as well to make it more strong. For example, to know what to install, head over to arch packages website, [ark (x86_64)](https://archlinux.org/packages/extra/x86_64/ark/)

You can install it with,
```bash
sudo pacman -S ark
```

Now on the same page, scroll down a bit, you'll notice,
-   [arj](https://archlinux.org/packages/community/x86_64/arj/ "View package details for arj") (optional) - ARJ format support
-   [lrzip](https://archlinux.org/packages/community/x86_64/lrzip/ "View package details for lrzip") (optional) - LRZ format support
-   [lzop](https://archlinux.org/packages/extra/x86_64/lzop/ "View package details for lzop") (optional) - LZO format support
-   [p7zip](https://archlinux.org/packages/extra/x86_64/p7zip/ "View package details for p7zip") (optional) - 7Z format support
-   [unarchiver](https://archlinux.org/packages/community/x86_64/unarchiver/ "View package details for unarchiver") (optional) - RAR format support
-   [unrar](https://archlinux.org/packages/extra/x86_64/unrar/ "View package details for unrar") (optional) - RAR decompression support
-   [extra-cmake-modules](https://archlinux.org/packages/extra/any/extra-cmake-modules/ "View package details for extra-cmake-modules") (make)
-   [kdoctools](https://archlinux.org/packages/extra/x86_64/kdoctools/ "View package details for kdoctools") (make)

We can avoid, **(make)** cause we are not building this! We just want to enhance it with more formats support. We can install those normally with `pacman -S` but later if you uninstall `ark`, these optional dependencies will be little hard to find. So here's what we will do, we can install those as dependencies, with the following command,
```bash
sudo pacman -S --asdeps --needed arj lrzip lzop p7zip unarchiver unrar
```

> **FLAGS**
>
> --asdeps    = as dependency.
>
> -- needed  = it won't reinstall if already exists in system.

- In the same way, let's install `gwenview` with optional dependencies as our image viewer. And it can even support `PSD` with optional dependency! Here you can install `qt5-imageformats` and `kimageformats` as optional.

- For text editing you can `kate`. You can use it simply or can enhance it with plugins. To enable LSP-server and markdown support, install it with full optional dependency.

- Now if you're thinking about power management, you can install `powerdevil`. With it you can mange your power settings right from your setting in plasma.

-  `plasma-systemmonitor` , a nice looking system monitor that you may want to try. You can also avoid it if you're happy with `htop` or anything else

- And finally for taking screenshots, we've `spectacle`. It has annotation support, and also it can integrate with your system perfectly if you're using KDE plasma!

> Upstream KDE has [package and setup recommendations](https://community.kde.org/Distributions/Packaging_Recommendations) to get a fully-featured Plasma session. Check this out for optional features!

### Recommendations
Now it's time to install your favorite packages, I guess. For the list of essential and well-refined packages for your system I've a list for you. Check,
- [Linux essential packages collection](/useful-linux-applications)

## Plasma Specials

### Spell check
Make sure `sonnet` is installed with `hunspell` or anything similar. And also don't forget to install a language pack for `hunspell`.

> If you install LibreOffice it'll be done automatically and I've a guide for you, check,
> - [LibreOffice extended installation guide](/libreoffice-extended)

### KDE Wallet Manager
You may find kde wallet whenever you connect your WiFi, or open your browser, asking for passwords. Instead of disabling it, you can actually use empty string as password. And then it won't ask for password anymore. Use `kwalletmanager` to set it up.

### KDE Connect
You can install `kdeconnect` to connect your phone with your system. It's a great tool to manage your phone from your system. You can also use it to share files, notifications, and even to control your system with your phone!

### Fonts
To enhance performance for terminal and other places you might want to Install `noto-fonts`, especially for `emoji-picker`,  `noto-fonts-emoji`.

There are some issues like, emojies doesn't work in the notification. To fix, edit the `/home/sharafat/.config/fontconfig/fonts.conf` and use the following lines,
```xml
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <alias>
  <family>sans-serif</family>
  <prefer>
   <family>Noto Sans</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
  </prefer>
 </alias>
 <alias>
  <family>serif</family>
  <prefer>
   <family>Noto Serif</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
  </prefer>
 </alias>
 <alias>
  <family>monospace</family>
  <prefer>
   <family>Noto Mono</family>
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family>
  </prefer>
 </alias>
 <dir>~/.local/share/fonts</dir>
</fontconfig>
```

> If above file doesn't exist, create one!

### Microsoft fonts
You can install `ttf-ms-fonts` to get Microsoft fonts. It's a good choice if you're working with Microsoft Office files. This package is available in AUR or chaotic AUR.

## Acknowledgements
For helping me to collect more information and revising, special thanks to,
- [Muhammed Naim](http://t.me/NaimsArchive)
- [Shahid Parvez](https://mrsnailo.github.io/)

## References
- [General recommendations - ArchWiki](https://wiki.archlinux.org/title/General_recommendations)
- [KDE - ArchWiki](https://wiki.archlinux.org/title/KDE)
- [GRUB/Tips and tricks - ArchWiki](https://wiki.archlinux.org/title/GRUB/Tips_and_tricks)
- [How to do a Minimal KDE Plasma Desktop Install in Arch Linux - Tuxinit](https://tuxinit.com/minimal-kde-plasma-install-arch-linux/)
