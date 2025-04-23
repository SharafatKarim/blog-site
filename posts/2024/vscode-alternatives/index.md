---
title: "vscode alternative :: code oss আর vscodium | পরিচয়, পার্থক্য, গুরুত্ব নিয়ে আলোকপাত"
date: 2024-08-08T19:18:35+06:00
lastmod: 2024-08-08T19:18:35+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: "Yet an another list of useful Applications that you can try in Android."
license: ""
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"
- name: "featured-image-preview"
  src: "featured-image.jpg"

tags: ["software", "basic", "internet", "computer"]
categories: ["software"]
summary: "যখন আপনাকে সিম্পল একটা টেক্সট ফাইল এডিট করতে বলা হবে, হয়তো নোটপ্যাড আছে। যতটুকু দরকার প্রায় সবই করা যাবে, তাই না? যারা একটু প্রোগ্রামিং সম্পর্কে ধারণা রাখেন, তারা হয়তো বলবে vscode এর কথা। তাহলে নোডপ্যাড আর vscode তো একই কাজের জন্য, তাই না?"

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

আসসালমু আলাইকুম। আশা করি ভালোই আছেন আপনারা। সত্য বলতে তাড়াহুড়ো করে লেখা, তাই ভুলগুলো ক্ষমাসুন্দর দৃষ্টিতে দেখার অনুরোধ রইলো।

## VS CODE

কথা না বাড়িয়ে চলে আসি vscode (visual studio code) নিয়ে। এটা একটা টেক্সট এডিটর। আসলেই কি তাই?

যখন আপনাকে সিম্পল একটা টেক্সট ফাইল এডিট করতে বলা হবে, হয়তো নোটপ্যাড আছে। যতটুকু দরকার প্রায় সবই করা যাবে, তাই না? যারা একটু প্রোগ্রামিং সম্পর্কে ধারণা রাখেন, তারা হয়তো বলবে vscode এর কথা। তাহলে নোডপ্যাড আর vscode তো একই কাজের জন্য, তাই না?

যারা নিয়মিত ব্যবহার করেন vscode, কেউ কেউ উত্তরস্বরূপ উপস্থাপন করতে পারেন, বিভিন্ন প্রোগ্রামিং ভাষার কোডের বিভিন্ন অংশ বিভিন্ন বর্ণে রঙিন হয়ে থাকে, এক কথায় syntax highligting। আবার কেউ বা অন্যান্য কিছূ সুবিধা যেমন, snippet, auto suggestion এর কথা স্মরণ করিয়ে দিবেন। আর কেউ বা extension এর কথাও বলতে পারেন। তবে আমি সেদিকে যাচ্ছি না আজ।

![vscode](https://grplusbd.net/wp-content/uploads/2024/05/image-4-1536x613.png)

যারা একেবারেই, vscode নিয়ে জানেন না তাদের জন্য একটি লিংক রেখে যাচ্ছি,
<https://code.visualstudio.com/>

## The Question

তাহলে এতটুকু ধারণা করা যায়, যে এটার মাধ্যমে আমরা সহজে কোড তো লিখতে পারবো। কিন্তু যেহেতু কোড বলে কথা, একটু তো প্রাইভেসি এর দরকার আছে তাই না? আপনি নিশ্চয়ই চাইবেন না যেনো, আপনার হাড়ভাঙা পরিশ্রমের লেখা কোড অন্য কোনো তৃতীয় পক্ষ তাদের মেশিন লার্নিং এ ব্যবহার করে। তাই না?

এই প্রাইভেসি সমস্যা সমাধানে, বেশ কয়েকটি উপায়ের মধ্যে, আমার দৃষ্টিতে সেরা উপায়টা হলো open source সফটওয়্যার ব্যবহার। আর vs code বলা যায় open source software। তাহলে সমস্যা সমাধান তো হয়েই গেলো। তাই না?

## The Twist

মজার ব্যাপার টা এখানে, যে আসলে সত্য বলতে কিছুই সমাধান হয় নি। vs code সম্পূর্ণরূপে open source না। কিছুটা proprietery এর ছোঁয়া রয়েই গেছে (source code)। আর আপনি এটাও জানেন না যে GitHub থেকে তারা exact code নিয়ে build করে নাকি কিছূ পরিবর্তন করে build করে। তাহলে উপায়?

এই প্রসঙ্গে পরিচয় করিয়ে দেই, দুটো বেশ জনপ্রিয় vs code এর open source alternative যাদের উৎপত্তি vs code থেকেই। তাহলে আমরা যদি এদেরকে vs code এর derivative বা সন্তান ধরি, আশা করি আমি ভুল নই। আমি দুটো বলেছি, তার মানে আবার এটা আপনারা ধরে নিয়েন না যে কেবল দুটোই আছে।

## VSCODIUM

Vscodium বলা যায় vscode এর উপর ভিত্তি করা সবচেয়ে জনপ্রিয় বিল্ড। এখানে microsoft এর টেলিমেট্রি গুলো ছাঁটাই করা হয়েছে, অপ্রয়োজনীয় dependency আর ঝামেলা মুক্ত। একেবারেই open source। বেশ মজার, তাই না?

এর website টা হলো, <https://vscodium.com/>

এখানে ভিজিট করে আপনারা হয়তো নিশ্চয়ই এর বৈশিষ্ট্য গুলো জেনে নিয়েছে। সেদিকে আমি না হয় নাই বললাম, আমি বরং সমস্যাগুলোতে ফোকাস করি। সমস্যার কথা যদি বলতেই হয়, তাহলে যেটা আপনাকে চিন্তিত করার জন্য যথেষ্ঠ সেটা হলো extension!

![vscodium](https://grplusbd.net/wp-content/uploads/2024/05/image-5.png)

হ্যাঁ, আপনি সব vs code এর extension পাবেন না। পাবেন না বলতে আমি বলতে চাচ্ছি বাম পাশের (by deafault তো বামেই থাকে তাই না?) extension এর store থেকে পাবেন না। তবে হ্যাঁ, আপনি চাইলে vs code এর official website থেকে extension bundle নামিয়ে তারপর install করতেই পারবেন। আর চাইলে vs code এর extension source entry ও করে নিতে পারবেন। বাকিটা আর বললাম না, কারণ আপনি নিশ্চয়ই এতোক্ষণে সার্চ ইঞ্জিনে এতোক্ষণে অনেক কিছূ খুঁজে নিয়েছেন। একটা লিংক রেখে গেলাম একপলকে step গুলো দেখে নিতে পারেন, <https://milicendev.netlify.app/article/install-vs-codium-and-integrate-vs-code-extensions/>

আরেকটা হয়তো ছোটখাটো চিন্তা মাথায় আপনার ক্রস করতে পারে, setting and account sync? সত্য বলতে vscodium এর setting.json টা আপনি backup রাখুন। extension এর বেলাতেও একই কথা প্রযোজ্য। একটা লিংক রেখে যাচ্ছি, <https://superuser.com/questions/1080682/how-do-i-back-up-my-vs-code-settings-and-list-of-installed-extensions> । আশা করি আপনারা নিজেরাই বুৃঝে গেছেন এতোক্ষনে।

## Code OSS

এটাও আরেকটা alternative vscode but vanilla। এটা তাদের জন্য যারা একটু সিকিউরিটি নিয়ে বেশীই concerned। সরাসরি microsoft কর্তৃক বানানো এবং কোনো telemetry বিহীন। আমি লিংক রেখে যাচ্ছি, 
- [GitHub - microsoft/vscode: Visual Studio Code](https://github.com/microsoft/vscode)

সাধারণত বিভিন্ন লিনাক্স ডিস্ট্রোগুলো by default এই package ship করে, যেমন, Arch Linux. এটা একটু বেশীই lightweight এবং হয়তো এখানে বেশ কিছূ proprietery extension একেবারেই কাজ নাও করতে পারে। একদম bare minimal বলে যদি কিছূ একটা থাকে তাহলে এর প্রকৃষ্ঠ উদাহারণ হতে পারে এই প্রজেক্ট। খুব সুন্দর একটা বিষয়, তাই না?

![code oss](https://grplusbd.net/wp-content/uploads/2024/05/image-6-1536x1152.png)

তাহলে কি আমরা এখানেও vscodium এর মতো extension যুক্ত করতে পারবো। অবশ্যই। বলা যায় একই প্রসেস। তবে যেহেতু code oss লিনাক্সে বেশী প্রচলিত তাই আপনি vs code এর marketplace যুক্ত করার জন্য আলাদা package ই পেয়ে যাবেন আশা করি। তাহলে তো কষ্ট কমে গেলো, তাই না?

যেমন, Archlinux এ আপনারা এই package পেয়ে যাবেন, Arch user repository তে, <https://aur.archlinux.org/packages/code-marketplace>

সত্য বলতে, ঠিক এইধরণের pacakge আপনারা vscodium এর জন্যও পেয়ে যাবেন। এবার পছন্দ আপনার!

## Wrapping up

এবার বিদায়ের পালা। আশা করি আপনার পোষ্ট টা উপভোগ করেছেন। তবে হ্যাঁ, আমি details এ কিছূই লেখি নি। আশা করি বাকি পথ আপনারা আপনার পছন্দের সার্চ ইঞ্জিনের সাথে চলতে পারবেন। আর প্রয়োজন হলে জানাতে পারেন। বিস্তারিত যদি কোনো স্টেপ জানার প্রয়োজন হয়। যেকোনো ভুল জন্য ক্ষমা করবেন। আজকের মতো এখানেই বিদায় নিলাম।

{{< admonition type=info title="মজার ব্যাপার," open=true >}}
এই আর্টিকেলটি আমার একজন বড় ভাই এর ব্লগসাইটের জন্য মূলত লেখা হয়েছিলো। এখান থেকে সেটা দেখে নিতে পারেন। এই পেইজের ইমেজগুলো সরাসরি সেখান থেকে লিংক করা।
{{< /admonition >}}
