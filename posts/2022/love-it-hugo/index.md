---
title: "Love It, Hugo"
date: 2022-10-19T11:59:01+06:00
lastmod: 2022-10-20T11:59:01+06:00
draft: false
author: ""
authorLink: ""
description: ""
license: ""
images: []

tags: ["hugo","internet","website","documentation","notes"]
categories: ["notes"]

featuredImage: "featured-image.jpg"
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

Umm, Love It, and hugo? What's going on?

> Hugo
>> A static site genarator

> Love It
>> Yet an another hugo theme

## What's big deal?

This article is mainly about `Love IT` theme's specialities but maybe you can go ahead to it's [repo](https://github.com/dillonzq/LoveIt) and learn for your own. So I'll be focusing on it's shortcodes which is an important element in hugo!

If you don't know about shortcodes then here's an example,
Writing,

```markdown
{{</* youtube ULDrp20nwfE  */>}}
```

will output,

{{< youtube ULDrp20nwfE  >}}

So, long story short, if you want to learn more about shortcodes check [Links and references](#links-and-references)

### Some useful shortcodes
What I like most is admonition! Also there are quite a few but I like it more than others. Here's some sample:

{{< admonition >}}
A **note** banner
{{< /admonition >}}

{{< admonition abstract >}}
An **abstract** banner
{{< /admonition >}}

{{< admonition info >}}
A **info** banner
{{< /admonition >}}

{{< admonition tip >}}
A **tip** banner
{{< /admonition >}}

{{< admonition success >}}
A **success** banner
{{< /admonition >}}

{{< admonition question >}}
A **question** banner
{{< /admonition >}}

{{< admonition warning >}}
A **warning** banner
{{< /admonition >}}

{{< admonition failure >}}
A **failure** banner
{{< /admonition >}}

{{< admonition danger >}}
A **danger** banner
{{< /admonition >}}

{{< admonition bug >}}
A **bug** banner
{{< /admonition >}}

{{< admonition example >}}
An **example** banner
{{< /admonition >}}

{{< admonition quote >}}
A **quote** banner
{{< /admonition >}}

### Admonition, it is!
So how do we actually use it? 🧐

Here's an input,
```markdown
{{</* admonition type=tip title="This is a tip" open=false */>}}
A **tip** banner
{{</* /admonition */>}}
Or
{{</* admonition tip "This is a tip" false */>}}
A **tip** banner
{{</* /admonition */>}}
```
And the output:
{{< admonition tip "This is a tip" false >}}
A **tip** banner
{{< /admonition >}}

{{< admonition quote "Fun Fact" false >}}
You know what? Above admonition part is directly copy pasted from Extended shortcodes part of Love It's documentation 😅
{{< /admonition >}}


## Links and references

Here are some links for faster access:
- [Hugo](https://gohugo.io/)
- [Love It repo](https://github.com/dillonzq/LoveIt)
- [Love It website](https://hugoloveit.com/)

And some links to some documentations:
- [Theme Installation](https://hugoloveit.com/theme-documentation-basics/)
- [Theme Installation Content](https://hugoloveit.com/theme-documentation-content/)
- [Markdown syntax](https://hugoloveit.com/basic-markdown-syntax/)
- [Emoji support](https://hugoloveit.com/emoji-support/)
- [Built in shortcodes](https://hugoloveit.com/theme-documentation-built-in-shortcodes/)

And some extended shortcodes:
- [Extended shortcodes](https://hugoloveit.com/theme-documentation-extended-shortcodes/)
- [Mermaid shortcodes](https://hugoloveit.com/theme-documentation-mermaid-shortcode/)
- [Echarts shortcodes](https://hugoloveit.com/theme-documentation-echarts-shortcode/)
- [Mapbox shortcodes](https://hugoloveit.com/theme-documentation-mapbox-shortcode/)
- [Music shortcodes](https://hugoloveit.com/theme-documentation-music-shortcode/)
- [Bilibili shortcodes](https://hugoloveit.com/theme-documentation-bilibili-shortcode/)
- [TypeIt shortcodes](https://hugoloveit.com/theme-documentation-typeit-shortcode/)

Happy content creation!

## FAQ

Do I need to learn html, css or anything else for generating static sites?
- Short answer, no. Long answer, maybe duckduckgo and Google can help you find it. 🎯

Is it free?
- Well, if you host on GitHub and don't need any domain just like me, then yeah! It's free.

Got any more question?
- Feel free to text me ✨

## Extra

Let me share a trick! In this website, you'll see headings starting with a vertical line or `#`, You can basically right click on them and copy a link which will work as a hyperlink to that specific Heading!

- [Read more here](https://sharafatkarim.github.io/markdown-syntax/) about markdown from me!
