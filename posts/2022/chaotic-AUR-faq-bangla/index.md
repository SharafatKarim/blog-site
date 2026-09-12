---
title: "Chaotic AUR সম্পর্কে কিছুটা প্রশ্ন উত্তর"
date: 2022-10-21T08:24:27+06:00
lastmod: 2022-10-21T08:24:27+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: ""
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"

tags: ["aur","archlinux"]
categories: ["linux"]

featuredImage: "featured-image"
featuredImagePreview: "featured-image"

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

## কেনো chaotic AUR?
  compile করতে হবে না  - সময় সাশ্রয়    আর মনে করেন আপনারটা ব্রাউজার AUR থেকে কম্পাইল করবেন <img class="emojione" alt="😅" title=":sweat_smile:" src="https://cdn.jsdelivr.net/emojione/assets/png/1f605.png?v=2.2.7">  আশা করি আর আপনাকে কিছু বলতে হবেনা <img class="emojione" alt="😆" title=":laughing:" src="https://cdn.jsdelivr.net/emojione/assets/png/1f606.png?v=2.2.7">

{{< admonition warning "Alert!" >}}
Chaotic AUR শুধুমাত্র archlinux বা, এর derivative, যেমন: endeavour os, archolinux এর জন্য। অবশ্য manjaro তেও কাজ করবে।
{{< /admonition >}}

  সাধারণত আমরা ব্রাউজার ৭০ মেগাবাইট বা এর কাছাকাছি কিছু একটা সাইজ দিয়ে নামাতে পারি কিন্তু যখন আপনি একটা ব্রাউজার কম্পাইল করবেন তখন আপনাকে সে ব্রাউজার যে প্রোগ্রামিং ল্যাঙ্গুয়েজ দিয়ে তৈরি সেই প্রোগ্রামিং ল্যাঙ্গুয়েজের কম্পাইলার ডাউনলোড করবে সোর্স কোড থেকে compile  করবে তারপর ইন্সটল করবে তারপর আবার ডিপেন্ডেন্সি গুলো আনইন্সটল করে দিবে এবার চিন্তা করে দেখেন কি পরিমাণ সময় লাগতাছে আর কি পরিমাণ ডাটা খরচ হচ্ছে <img class="emojione" alt="😅" title=":sweat_smile:" src="https://cdn.jsdelivr.net/emojione/assets/png/1f605.png?v=2.2.7">    যেমন: বাস্তব অভিজ্ঞতা,  <img src="https://2img.net/i/fa/i/smiles/icon_king.png" alt="king" longdesc="52">    enve  (compile করা ভার্সন 70 MB এর কাছাকাছি)    কিন্ত যখন সোর্স কোড থেকে build করবো  সোর্স কোড (হয়তো সর্বোচ্চ 2 থেকে 3 মেগাবাইট)  dependency (বিশ্বাস করুন আর না করুন এটা ডিপেন্ডেন্সি 2gb থেকেও বিশাল বড়)  তারপর আবার সোর্স থেকেbuild করতে কি পরিমান যে সময় লাগবে সেটা আপনি নিজে চেষ্টা না করলে বুঝবেন না    BTW, এই enve সফটওয়্যার chaotic AUR এ নাই, অর্থাৎ আপনাকে appimage বা flatpak এর আশ্রয় নিয়ে হবে    অথবা কোনো দয়াবান যদি কম্পাইল করে  .pkg.tar file টা নিয়মিত আপলোড করে

## fun fact <img src="https://2img.net/i/fa/i/smiles/icon_flower.png" alt="flower" longdesc="59">
enve software হুবহু adobe after effects এর মত ইন্টারফেস আর অ্যানিমেশন লেভেল অনেক high অথচ অধিকাংশ মানুষ জনেও না, contribute ও করে না, আর এখনো alpha stage এ রয়ে গেছে

## Extra <img src="https://2img.net/i/fa/i/smiles/icon_santa.png" alt="santa" longdesc="49">

### pacakge availability
আর AUR এর কেবল ইম্পর্ট্যান্ট আর বেশি vote আছে এরকম pacakge chaotic AUR এ আছে, chaotic AUR তেমন বড়সর কিছুই না, এবং chaotic AUR এ কমন অনেক কিছুই নাই

## কিভাবে তাহলে ইন্সটল করবেন?
সোজা তাদের [Official website](https://aur.chaotic.cx/) এ চলে যান, সেখানে বিস্তারিত বলা আছে!

{{< admonition tip "আরেকটি কথা!" true >}}
আপনি চাইলে অবশ্য terminal এ একটি লেখা রান করে আমার তৈরি একটা script এর মাধ্যমে chaotic AUR install করতে পারবেন। বিস্তারিত এই লিংকে পাবেন:
- [Chaotic AUR installation script](https://github.com/SharafatKarim/chaotic-AUR-installer)

হয়তো এই বিষয়ে আরেকটি post লিখবো 😅
{{< /admonition >}}
