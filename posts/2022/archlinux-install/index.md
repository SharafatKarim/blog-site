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

# Introduction

In this guide I'll be installing Arch Linux with BTRFS. And in a separate article I'll show you the way to a minimal KDE plasma desktop along with some extended possibilities. If you're reading this I can assume you are already familiar with [archwiki](https://wiki.archlinux.org/) - a great place to learn about Arch Linux!

## Why Arch?

If you don't have much idea about different distros, maybe you can read this [article](https://wiki.archlinux.org/title/Arch_compared_to_other_distributions). Also you'll find a lot of guys in YouTube for this purpose (to explain you why you need arch). If you've much free time to tinker with your system and you are in need of a full time job with no salary, welcome to the arena! I'll highly recommend you to try Arch Linux. 

## Why BTRFS?

You might be familiar with [computer storage formats](https://en.wikipedia.org/wiki/Journaling_file_system) like ntfs, fat32 or exfat. BTRFS (better F S ) is just like that with copy-on-write principal. As Arch Linux is a rolling model, often called bleeding edge, system will be updated a lot and a lot of things can break or repair on each update.

Let me give you an example, 