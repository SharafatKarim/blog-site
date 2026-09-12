---
title: "আমার দেখা একটি সেরা Linux distro (manjaro Linux)"
date: 2022-10-21T06:03:15+06:00
lastmod: 2022-10-21T09:03:15+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
images: []
resources:
- name: "featured-image"
  src: "best-linux-distro.png"
- name: "featured-image-preview"
  src: "best-linux-distro-thumbnail.png"

tags: ["linux", "manjaro"]
categories: ["linux"]

featuredImage: "featured-image"
featuredImagePreview: "featured-image-preview"

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

summary: "Manjaro সর্বপ্রথম ব্যবহার যোগ্য distro হওয়ার পিছনের কারণসমূহ"

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

## কেনো <strong>Manjaro</strong>?
 Manjaro বেশি ইউজার ফ্রেন্ডলি এবং সময় সাশ্রয়কারী হবে বলে আমি মনে করি। শুধুমাত্র PAMAC(সফটওয়ার store) এর জন্যে। ডেবিয়ান রিপো গুলোতে সব সফটওয়্যার পাওয়া যায় না। ফ্ল্যাটপ্যাক ও অপূর্ণ। দেখা যায় অনেক সফটওয়্যার .deb অথবা ইনস্টলেশন স্কিপ্ট ইউস করে ইন্সটল করতে হচ্ছে। অন্যদিকে যদি কোনো সফটওয়্যার লিনাক্সের জন্য এভেলএবল থাকে, তা প্যামাকে পাওয়া যাবে। শুধু ক্লিক করার অপেক্ষা। কোনো ঝামেলা নাই। প্যামাকে একই সাথে আর্চ, মানজারো, আর্চ ইউজার রিপো, ফ্ল্যাটপ্যাক, স্ন্যাপ সব সোর্স থেকে সফটওয়্যার পুল করে। একারণেই নতুন ইউজারদের জন্য manjaro বেশি সুবিধাজনক। আর শুধুমাত্র স্টেটেবিলিটির খাতিরে ডেবিয়ান বেজড ডিস্ট্রো রেকমেন্ড করা ঠিক হবে না। Manjaro semi rolling distro। তাই আর্চ থেকে অনেক বেশি stable।
 <img src="https://www.fossmint.com/wp-content/uploads/2018/04/Pamac-Pacman-GUI-for-Arch-Linux.png" alt="আমার দেখা একটি সেরা Linux distro (manjaro Linux) Pamac-Pacman-GUI-for-Arch-Linux">

## Personal experience
 সবার বেশ পরিচিত একটা সফটওয়ার inkscape। Inkscape এর version 1.0.1 এ extension কাজ করতো না এবং কিছু bug ছিলো যা লেটেস্ট version এ ছিলো না (এটা প্রায় 1 বছর আগের ঘটনা)। তো Ubuntu তে যদি আমার কোনো software আপডেট করার প্রয়োজন হতো 6 মাস অপেক্ষা করা লাগতো। অথবা ppa add করতে হতো। আর ppa add করা user friendly না, এবং মাঝে মাঝে release file না থাকায় কাজ ও করে না। এক্ষেত্রে snap বা flatpak ইউজ করতে হতো। Snap আর flatpak এর download সাইজ বিশাল বেশি এবং এখানকার inkscape full featured না, অনেক extension কাজ করবে না। কারণ snap আর flatpak সিস্টেম হতে বিচ্ছিন্ন পরিবেশে কাজ করে এবং library share করে না। সবচেয়ে বড় অসুবিধা, ppa, snap আর flatpak এ bdix স্পীড নাই। কিন্তু Manjaro তে নিজের রিপো তে latest version available। সাইজ ও কম, bdix speed ও available।
 <img src="https://2img.net/i/fa/i/smiles/icon_wink.gif" alt="Wink" longdesc="15">  <img src="https://i1.wp.com/gamblisfx.com/wp-content/uploads/2017/03/pamac-gui.png?w=922&amp;ssl=1" alt="আমার দেখা একটি সেরা Linux distro (manjaro Linux) Pamac-gui">

## Software Installation
 এবার আসি সফটওয়ার installation নিয়ে। Ubuntu তে chrome কিভাবে ইনস্টল করেন? .Deb file website থেকে download করতে হয় তারপর সেটা gdebi বা store এর সাহায্যে ইনস্টল করতে হয়। আবার মনে করেন আপনি xdm ইনস্টল করবেন। এক্ষেত্রে Ubuntu based system এ xdm এর ওয়েবসাইটে গিয়ে zip file download করে তারপর terminal এ সেই ডিরেক্টরি তে গিয়ে bash script run করতে হবে (যদি executable হয়। আর তা না হলে আপনার এটাকে executable করে নিতে হবে)। এরকমভাবে natron ও অন্যান্য software এর plug in আপনাকে ওয়েবসাইট থেকে ডাউনলোড করে নির্দিষ্ট জায়গায় copy paste করতে হবে। &nbsp;অথচ Manjaro তে যেহেতু AUR কাজ করে তাই এক ক্লিক এ chrome, xdm install, plug in install করতে পারবেন।
 <img src="https://maboxlinux.org/wp-content/uploads/2020/03/pamac_gui.png" alt="আমার দেখা একটি সেরা Linux distro (manjaro Linux) Pamac_gui">

 পাশাপাশি Manjaro এর store থেকে wallpaper, GTK/ qt theme, icon pack, cursor, font, gimp এর brush, template, inkscape এর extension, ব্রাউজার এর ffmpeg লাইব্রেরী প্রায় সব download এবং ইনস্টল করতে পারবেন। পাশাপাশি দাভিঞ্চি resolve এর মত premium software।
 <img src="https://maboxlinux.org/wp-content/uploads/2020/03/pamac_pref_aur.png" alt="আমার দেখা একটি সেরা Linux distro (manjaro Linux) Pamac_pref_aur">

 অনেকের প্রশ্ন Manjaro bleeding edge। তাই স্ট্যাবল না। কিন্ত Manjaro semi-rolling distro (direct rolling না)। কোনো software release হওয়ার পর Manjaro এর developer রা টেস্ট করে এবং অন্যান্য bug report এর প্রতি নজর রাখে। তাই সফটওয়ার এর new version আসতে প্রায় 1-2 সপ্তাহ সময় লাগে। তাই Manjaro আপনি যতটা চিন্তা করেন তার চেয়ে অনেক stable। আমি অনেক দিন ধরে ব্যবহার করছি এবং এখনও break করে নি। In fact আমি time shift বা backup ও করিনা। আমার কথা বিশ্বাস না হলে Manjaro forum এ দেখেন কতজনের সিস্টেম break করেছে।
 <img src="https://maboxlinux.org/wp-content/uploads/2020/03/pamac_pref_general.png" alt="আমার দেখা একটি সেরা Linux distro (manjaro Linux) Pamac_pref_general">

 তাই পরিশেষে Manjaro ভালো লাগার সবচেয়ে বড় কারন হলো এর সফটওয়ার store (pamac)। আপনার যদি কখনো snap বা flatpak দরকার হয়, আপনি store থেকেই install করতে পারবেন। তবে snap avoid করার পরামর্শ রইলো কারণ এটা boot time কমিয়ে দেয়। যারা advanced user তাদেরকে বলবো Manjaro minimal টা try করার জন্য। এটা অনেক lightweight এবং boot time কম।<img src="https://2img.net/i/fa/i/smiles/icon_cool.gif" alt="Cool" longdesc="6">

{{< admonition abstract "BTW" true >}}
 এটা আমার সম্পূর্ণ নিজের perspective। আর আমি এটাও বলছি না, Manjaro best। installation, বা ব্যবহার সম্পর্কিত পরামর্শ বা আলোচনা করার জন্য আমাদের [telegram group](https://t.me/LinuxUniverse) join করার অনুরোধ রইল!
{{< /admonition >}}

## সমস্যাসমূহ
মানুষের তৈরি কোনো কিছুই তেমন একটা *perfect* না। আর তাই আমি মনে করি সমস্যা থেকে পালানোর চেয়া আমরা অন্তত তা সমাধানের চেষ্টা করতে পারি।

Manjaro বেশ common একটি সমস্যা হচ্ছে Bangla font (display) নিয়ে। Telegram, discord বা, firefox এ এই সমস্যা প্রায় common। তাই সমস্যাটি সমাধানের জন্য আমি একটি script লিখেছি, চাইলে [GitHub repo]() চেক করে দেখতে পারেন। সমস্যাটি সমাধানের জন্য নিচের কোডটি terminal এ রান করাই যথেষ্ঠ। তারপর simply log out করে log in করলেই হবে।

```bash
curl -s https://raw.githubusercontent.com/SharafatKarim/Manjaro-Bangla-Font-Fix/main/main.sh | bash
```

> Restart করতে হবে না?
>> We don't do that here 😆
