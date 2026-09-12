---
title: "Software Telemetry কি | Basic Concepts"
date: 2022-10-21T08:44:28+06:00
lastmod: 2022-10-21T08:44:28+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["computer","basic","software"]
categories: ["software"]

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
আমরা অনেকেই সফটওয়্যারের বিভিন্ন খবরে এই টার্মটির সাথে পরিচিত হই। কখনো কি ভেবে দেখেছেন কি এই টেলিমেট্রি? বাংলা ভাষায় টেলিমেট্রি বলতে বিভিন্ন সংজ্ঞা থাকতে পারে। সেদিকে যাবো না, আপনি চাইলে কিছু প্রয়োগ এই লিংক থেকে দেখে নিতে পারেন।
- [Stackify- telemetry tutorial](https://stackify.com/telemetry-tutorial/)

{{< admonition quote "Alexandra Altvater এর মতে," true >}}
Telemetry is the automatic recording and transmission of data from remote or inaccessible sources to an IT system in a different location for monitoring and analysis. Telemetry data may be relayed using radio, infrared, ultrasonic, GSM, satellite or cable, depending on the application (telemetry is not only used in software development, but also in meteorology, intelligence, medicine, and other fields).
{{< /admonition >}}


আমরা বিভিন্ন সময় বিভিন্ন licence এর সফটওয়্যার ব্যবহার করি। যেমন: propriety, open source, free, freeware ইত্যাদি। কিন্তু কখনো কি ভেবে দেখেছেন, এসব সফটওয়্যারের মালিকগণ কিভাবে টাকা ইনকাম করে?

## Premium or paid
প্রিমিয়াম বা পেইড সফটওয়্যারের ক্ষেত্রে সাধারণত তারা সরাসরি লাইফটাইম বা নির্দিষ্ট সময়ব্যাপী লাইসেন্স বিক্রি করে থাকে। আবার এক্ষেত্রে ভোক্তাদের দৃষ্টি আকর্ষণ এর উদ্দ্যেশ্যে বিনামূল্যে কিছু trial ও অফার করা হয়ে থাকে। আবার কখনো কখনো দেখা যায়, শিক্ষার উদ্যেশ্যে বিনামূল্যে বিতরণ করা হয়ে থাকে।

## Open source
আবার open source এর ক্ষেত্রে মালিকগণ সম্পূর্ন সোর্স কোড ইন্টারনেটে দিয়ে দেয় এবং এতে তার কোন ব্যাক্তিস্বার্থ থাকে না। কাজটা বর্তমানে সবচেয়ে বেশি প্রশংসনীয় এবং এতে মহত্যের একটি বিশালতার পরিচয় পাওয়া যায়। এরকম একটি জনপ্রিয় প্রোজেক্ট হলো Linux kernel।

## Freeware
আবার freeware সফটওয়্যারের ক্ষেত্রে দেখা যায়, যে, মালিকগণ সফটওয়্যারে বিজ্ঞাপন ব্যবহার করেন এবং ইনকাম করে থাকেন। কাজটি কিন্তু নিন্দনীয় নয় বরং বিজ্ঞাপন থেকে যে ইনকাম আসে সেটা মালিককে সফটওয়্যার development এ আরও motive করে।

## Free
এজাতীয় সফটওয়্যার অনেকটা open source এবং freeware এর মাঝামাঝি বলা যায়। এতে সফটওয়্যার এর source code কম্পাইল করা থাকে, অর্থাৎ, তা উন্মুক্ত নয়, কেবল developer এর কাছে থাকে। তবে সফটওয়্যরের ভিতরের প্রায় সকল সুযোগ সুবিধা  সম্পূর্ণ বিনামূল্যে পেয়ে যাবেন।


## Evil type
এবার আসি আরও একটি ভিন্ন ক্যাটাগরি যা at least আমার কাছে নিন্দনীয়। এক্ষেত্রে সফটওয়্যারটি আপনার ডিভাইসের ডাটা সংগ্রহ করে এবং আপনার অজান্তে বা আপনার অনুমতি সাপেক্ষে ডাটা তাদের সার্ভারে যুক্ত করে। কাজ কিন্তু এখানেই শেষ নয়। তারা টাকার বিনিময়ে অন্য কোনো বড় প্রতিষ্ঠানের কাছে টাকার বিনিময়ে বিক্রি করে, যা আপনার ডেটার খারাপ ব্যবহার করতে সক্ষম।

এক্ষেত্রে developer আবার কখনো কখনো সফটওয়্যার tracker যুক্ত করে রাখে যা নিন্দনীয় একটি কাজ। তাই সাবধানে ব্যবহার করার পরামর্শ দেয়া যায় 😅। এই লাইনটি Premium, Freeware, Free এই ৩ ক্ষেত্রেই প্রযোজ্য।

আর এভাবে আপনার ডেটা trace করে তাদের সার্ভারে পাঠানোর প্রক্রিয়াই হলো telemetry এর বেসিক। আমি আপনাকে বেসিকটা ধরিয়ে দিলাম, এবার এ সম্পর্কে আরও জানতে আপনি ইন্টারনেটে English কিছু article পড়তে পারেন। কারন এই সম্পর্কে আমি নিজে google এ কিছু খুজে পেলাম না। আপনারা পাইলে কমেন্টে জানিয়েন, সবার শিখতে উপকার হবে।

{{< admonition info "BTW," true >}}
উপরে আমি যে evil type, free, freeware এজাতীয় শ্রেণীতে বিভক্ত করলাম, ব্যাপারটা পুরোটাই মনগড়া। বুঝানোর সুবিধার জন্য। আরো বিস্তারিত জানতে হাঁস, গুগল মামা তো আছেই। চাইলে আমাদের সাথেও আলোচনা করতে পারেন [এখানে](https://t.me/LinuxUniverse)।
{{< /admonition >}}
