---
title: "Font এবং glyph পরিচিতি (পর্ব ১)"
date: 2022-10-21T08:06:07+06:00
lastmod: 2022-10-21T08:06:07+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: ""
license: ""
images: []
resources:
- name: "featured-image"
  src: "font-glyph-1.jpg"

tags: ["font", "computer", "basic"]
categories: ["computer"]

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

## Font কি?
   ফন্ট কি সেটা আমরা কমবেশি সবাই জানি, সংজ্ঞা জানাটা তেমন গুরুত্বপূর্ণ নয়। আজকের পোষ্টে আলোচনা করবো, ফন্ট আর গ্লিফের মধ্যাকার সম্পর্ক নিয়ে। তো যদি ফন্ট কাকে বলে বলতে চাই, এভাবে চিন্তা করতে পারি, লেখার প্রকাশের ধরণ। আচ্ছা আরও সহজ করে বলি, আমরা অনেকেই হয়তো <i>Microsoft Word</i> বা কোনো <i>word processing</i> সফটওয়্যারে কাজ করেছি। সেখানে আমরা কোনো একটা লেখার সাজ সজ্জা পরিবর্তন করতে, সাধারণত home tab এর অধীণে বিভিন্ন ফন্ট স্টাইল ব্যবহার করে থাকি। তাহলে সহজে সংজ্ঞায়িত করতে চাইলে, বলতে পারি, যা লেখার প্রদর্শনের ধরণ ইঙ্গিত করে সেটাই ফন্ট।  Wikipedia অনুযায়ী,
   <blockquote>
      <div>&nbsp; &nbsp;In metal typesetting, a font is a particular size, weight and style of a typeface. Each font is a matched set of type, with a piece (a “sort“) for each glyph, and a typeface consisting of a range of fonts that shared an overall design.</div>
   </blockquote>
    উপরের সংজ্ঞা থেকে যে idea টা আমাদের মাথায় সর্বপ্রথম আসে, সেটা হলো, যে ফন্ট size, weight এবং স্টাইল (typeface), এই ৩টি ডেটা নিয়ে মূলত কাজ করে। আমি এই আর্টিকেলে আপাতত definition গুলো clear করার চেষ্টা করবো,

## Font এবং typeface পরিচিতি
যদি প্রশ্ন করা হয়, একটি পাখির ছবি share করেন, তবে আপনি কোন পাখির ছবি share করবেন? অবশ্যই পাখি বলতে আপনি cordata পর্বের aves taxonomic class কে ইঙ্গিত করছেন যার অধীনে লক্ষ লক্ষ পাখির প্রজাটি, যেমন: দোয়েল থাকতে পারে। অনুরূপভাবে, একটি বর্ণের অসংখ্য চেহারা থাকতে পারে যা কেবলমাত্র একটি বর্ণকেই ইঙ্গিত করবে। তবে সেই চেহারাগুলো হলো font এবং শব্দটা হলো বর্ণ।

## Font এবং glyph পরিচিতি
সাধারণত glyph বলতে আমরা বুঝি একটি vertical mark বা চিহ্ন যা অবশ্যই অর্থবোধক হতে হবে। কি দরকার? simple, কোন নির্দিষ্ট একটি মনোভাব। এভাবে চিন্তা করুন, ছোটবেলায় পরীক্ষার হলে আমাদের অনেকে বহুনির্বাচনী একে অন্যকে দেখানোর জন্য হাতের ইশারা ব্যবহার করতাম/ করি। তো এখন অনেক ইশারা এমন যে তা কেবলমাত্র আপনার বন্ধু বা আপনাদের বুঝতে কোন অসুবিধা হচ্ছে না। আপনার হাতে আঙ্গুল ছোট নাকি বড় বা আপনি বাম হাত তুলছেন নাকি ডান হাত তুলছেন সেটার উপর নির্ভর করছে না। আপনি যেভাবেই ইশারা করুন না কেন, আপনার বন্ধু কিন্তু ঠিকই আপনি যা বলতে চাচ্ছেন তা বুঝতে পারছে অনতিবিলম্বে। আমার কথা বিশ্বাস করুন আর না &nbsp;করুন, এটাই glyph।

এখানে যে একটি নির্দিষ্ট চিহ্ন একটি শব্দের প্রতিনিধিত্ব করছে সেটাই glyph।  সহজ কথা আমি কেনো এত জটিল করছি?  আচ্ছা আমি উপরে যা যা বললাম, তা কিন্তু আমি বাংলা ভাষার রেফারেন্স টেনে মাত্র ৪ লাইনেই ব্যাখ্যা করতে পারতাম, এতো প্যাঁচাচ্ছি কেনো?

কারণ font কেবল একটি ভাষার উপরই applicable নয়, সেটা আরও বেশি symbol কভার করে।  সহজভাবে চিন্তা করুন, অনেকে android এ play store থেকে বিভিন্ন স্টাইলিশ কীবোর্ড ব্যবহার করে টাইপ করি এবং মনে করি যে ভিন্ন ফন্ট ব্যবহার করে লিখছি, &nbsp;আসলেই কি তাই?

আচ্ছা একটি experiment করে দেখি-  &nbsp; &nbsp;একটি ফোল্ডার তৈরি করুন &nbsp; &nbsp;নামকরণের ক্ষেত্রে আপনার stylish কোনো একটা কিবোর্ড ব্যবহার করুন &nbsp; &nbsp;পরবর্তীতে normal keyboard এর সাহায্যে সেই ফাইলটি search করে খুঁজে বের করার চেষ্টা করুন  আমি আপাতত উত্তর আপনাদের উপর ছেড়ে দিলাম। তো উত্তর আপনারা চাইলে কমেন্টে জানাতে পারেন।

আচ্ছা তাহলে কেনো এমনটা হলো?  চলুন আবার সেই আগের উদাহারণের সাহায্যে ব্যাখ্যা করার চেষ্টা করি। আপনাকে আমি দোয়েল আর ময়না পাখি যদি দেখাই আপনি যদি দুইটিকেই পাখি বলেই অভিহিত করেন, তাহলে আপনি কিন্তু সঠিক। কিন্তু আপনি যদি দোয়েলকে ময়না বলেন তাহলে আপনি কিন্তু ভুল। ঠিক তেমনই স্টাইলিশ কীবোর্ডের যেই শব্দকে আপনি ইংরেজী বা অন্য কোনো ভাষার শব্দ বলে বিবেচনা করে আসছেন, সেটা কিন্তু আদৌ সেই ভাষার শব্দ নয়। সহজ কথায়, তাদের glyph ভিন্ন ভিন্ন। আবার আপনি যখন microsoft word/ Libre Office এ কোনো একটি বর্ণকে ভিন্ন ভিন্ন ফন্ট apply করেন তবে দুইটিই কিন্তু সেই বর্ণই থেকে যাবে, অর্থাং তারা পরষ্পরের ফন্ট এবং সেই বর্নটি হলো typeface। আশা করি কিছুটা হলেও idea clear হয়েছে। এবার আপনারা কয়েকটি article পড়লেই full concept clear হয়ে যাবে। পাশাপাশি নিজেদের মাঝে আলোচনা করতে পারেন, পাশাপাশি আমাদের টেলিগ্রাম গ্রুপে আমাদের সাথে আলোচনা করতে পারেন।  ইন শা আল্লাহ আপনারা আগ্রহী হলে, font আর glyph মডিফাই বা তৈরি সম্পর্কিত আর্টিকেল সময় পেলে লিখবো।


{{< admonition info "First appearance" >}}
This article was previously published by me in-

- [Shop Tips 24](https://shoptips24.com/education-guideline/3716/)
- [Linux Bangla](https://linuxbangla.forumotion.asia/t30-font-glyph)
{{< /admonition >}}
