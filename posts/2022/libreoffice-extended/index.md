---
title: "Libreoffice Extended Installation"
date: 2022-11-08T08:03:12+06:00
lastmod: 2022-11-08T08:03:12+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: "A proper way to do some extended checkups and troubleshooting for LibrOffice."
license: ""
images: []

tags: ["linux","software","office"]
categories: ["software"]
summary: "A proper way to do some extended checkups and troubleshooting for LibrOffice."

featuredImage: "featured-image.jpg"
featuredImagePreview: "featured-image.jpg"

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

A proper way to do some extended checkups and troubleshooting for LibrOffice. So that while using you don't have to worry much about any missing feature like spelling correction not working, or similar. So then, let's extend our possibilities!

{{< admonition warning "Requirements," >}}
This guide is for Linux users only. If you use flatpak or snap, you can avoid [first section](#regular-installing). I'll assume you have enough knowledge on installing a package, given it's name.

Here, my commands will only work on ArchLinux and it's derivatives but the process is almost same for any distro.
{{< /admonition >}}

## Regular installation
Regular installation is not a big deal. You'll easily find LibreOffice in your distro's official repo. For Arch or Manjaro there might be 2 different packages, fresh and still. Choose the fresh one. The following command should do the trick,

```bash
sudo pacman -S libreoffice-fresh
```

If you're using a Ubuntu or similar point release based distro, you can still install the latest stable [through PPA](https://www.ubuntuupdates.org/ppa/libreoffice), in case you are not happy with [flatpaks](https://flathub.org/apps/details/org.libreoffice.LibreOffice) or [snap package](https://snapcraft.io/libreoffice).

{{< admonition tip "And," >}}
if you're concerned about dark GTK theme of LibreOffice, you can install [libreoffice-qt](https://packages.ubuntu.com/focal/libreoffice-qt5) package. (for GNOME/GTK users only)
{{< /admonition >}}

## Language package
LibreOffice comes with `en-US` language package by default. But that's not all. You can include more language. For example I also need `Bangla` spelling feature. So in this case I'll install `libreoffice-fresh-bn`.

```bash
sudo pacman -S libreoffice-fresh-bn
```

If your'e comfortable with `Bangla (India)` then, you've to install `libreoffice-fresh-bn-in` package. A good way to find all the language package is [through Arch Wiki](https://archlinux.org/packages/?sort=&q=libreoffice-fresh-&maintainer=&flagged=). You can also find more in the AUR.

## Spelling
For spelling LibreOffice use `hunspell`. Make sure it's installed. My primary language `Bangla` isn't available here yet! But you can try to look in the packages for your language. In Arch to make sure `hunspell` and `English-US` is included, following command may help you,
```bash
sudo pacman -S --needed hunspell hunspell-en_US
```
If your language is not supported officially then you can still extend it's possibility using extensions. For `Bangla` language I'll use the following extension,
- [Bengali Spellchecker Dictionary](https://extensions.openoffice.org/en/project/bengali-spellchecker-dictionary)

{{< admonition warning >}}
This extension was not updated recently. So it's not recommended of course, but we'll really appreciate if anyone develops it for us. And if anything exits similar, please leave a comment.
{{< /admonition >}}

## Hyphenation
In case your want to add more rule on Hyphenation you can try this package. Rules on English should be enough but you may also look at the available packages. Following command will work to install it on Arch,
```bash
sudo pacman -S --needed hyphen hyphen-en
```
If your language is not supported officially then you can still extend it's possibility using extensions. Likewise, for `Bangla` language I'll use,
- [Bengali(India) Hyphenation Dictionary](https://extensions.openoffice.org/en/project/bengaliindia-hyphenation-dictionary)

## Thesaurus
For `thesaurus` you can find the supported language [here](https://archlinux.org/packages/?sort=&q=mythes&maintainer=&flagged=). If you want to set it for English language, you may try the command,
```bash
sudo pacman -S --needed libmythes mythes-en
```
Not available for your language? Check [Extensions](#extensions). And yeah! In this era, search engine exist to define something!

## Grammar checking
For grammar checking most common way is to use [Language tool.](https://www.languagetool.org/) It's quite popular. To use it,
- download it's extension [from here](https://extensions.libreoffice.org/en/extensions/show/languagetool) (*.oxt file). Latest version is recommended. File size is around 160 MB.
- manually install it in LibreOffice through Tools > Extension. (ctrl + alt + e)
![](https://res.cloudinary.com/dte603aka/image/upload/v1667876796/blog/2022/Screenshot_20221108_090549-1_isfwdu.png)

After installation, got an additional toolbar? If you don't like it [you can remove it also.](#extra-toolbar)
{{< admonition warning "Confused?" false >}}
This tool is for Grammar checking, not for spelling check.

![](https://res.cloudinary.com/dte603aka/image/upload/v1667877281/blog/2022/Screenshot_20221108_091352_loo2bd.png)

For spelling check, read top sections.
{{< /admonition >}}

## Extensions
You can enhance your libreoffice experience with a lot of extensions. So where will you find extensions? Try these  sources,
- [Libre planet](https://libreplanet.org/wiki/Group:OpenOfficeExtensions/List)
- [Libre Office extensions](https://extensions.libreoffice.org/)
- [Open Office extensions](https://www.openoffice.org/extensions/index.html)
- [Further Open Office extensions](https://extensions.openoffice.org/)

{{< admonition tip "And, another thing" >}}
Every single `Open Office` extensions will work perfectly in LibreOffice No need to worry!
{{< /admonition >}}

## Look & Feel
If you're coming from `Microsoft Office` this section is just for you!

Libre Office's default interface is similar to Open Office. You can change it to tabbed mode like Microsoft office. To do so,
- From menubar, view, select `User Interface...`

![](https://res.cloudinary.com/dte603aka/image/upload/v1667880430/blog/2022/Screenshot_20221108_100657_qfuosk.png)

- try `tabbed` or play with them 🎃

![](https://res.cloudinary.com/dte603aka/image/upload/v1667880531/blog/2022/Screenshot_20221108_100821_jgdqcu.png)

- finally `apply`

{{< admonition warning "And also, plasma or QT users," >}}
Tabbed interface or anything other than default may not respect your theme (breeze or breeze-dark) especially if you're using dark theme!

![](https://res.cloudinary.com/dte603aka/image/upload/v1667880812/blog/2022/photo_2022-11-08_10-13-19_ivkfyz.jpg)

If this is the case, try `kvantum` theme engine to change your QT theme. I use `qogir-qt` and here's the look,

![](https://res.cloudinary.com/dte603aka/image/upload/v1667880997/blog/2022/Screenshot_20221108_101502_cx4ah8.png)

{{< /admonition >}}

And finally, if you totally want to completely mimic Microsoft Office like look then YouTube can help you! Here's some hint,
- a similar icon package
- change default font
- change keyboard shortcuts (not much necessary)
- change default file export type

## Auto language detect
You just have to manually detect the language once in a doument, and from onward it'll detect the rest of the document automatically! Check the following video from web or telegram,

- [:(fa fa-solid fa-play):   Video Stream (WEB)](https://res.cloudinary.com/dte603aka/video/upload/v1667884439/blog/2022/libre-bangla-autocorrect_pyclwc.mp4)
- [:(fa fa-solid fa-video):   Video in Telegram channel](https://t.me/SharafatsNotes/280)

## Troubleshooting

### Icons - not visible
Icons are not visible in the dark theme? Well, you know icons have black color by default and in the dark theme icons canvas/ background is also black/ dark. So, dark foreground + dark background = nothing 😅.

The solution is to use a dark icon variant like, `breeze-dark`, instead of `breeze` or any light variant.

Change the icon style in
- Tools > Options (alt + F12)
- LibreOffice > View > Icon Style

to `Breeze Dark` or another readable icon style. You may need to install the `breeze-gtk` package.

![](https://res.cloudinary.com/dte603aka/image/upload/v1667879757/blog/2022/photo_2022-11-08_09-55-34_aetlrt.jpg)

### Extra toolbar
If you've extra toolbars like this one,

![extra toolbar](https://res.cloudinary.com/dte603aka/image/upload/v1667877560/blog/2022/Screenshot_20221108_091852_hirad5.png)

From the menubar, view, Toolbars, disable corresponding entry.

![](https://res.cloudinary.com/dte603aka/image/upload/v1667877708/blog/2022/Screenshot_20221108_092125_zkaqnj.png)
