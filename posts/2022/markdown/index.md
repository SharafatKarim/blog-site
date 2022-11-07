---
title: "Markdown Syntax"
date: 2022-10-20T08:22:05+06:00
lastmod: 2022-10-20T08:22:05+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: ""
license: ""
images: []

tags: ["notes","markdown","html"]
categories: ["notes"]

featuredImage: "featured-image.png"
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

This article shows some useful and daily-driver type syntax, that I may use daily. First, right after heading, one example , followed by it's syntax. I won't explain though 😅.

{{< admonition >}}
  To learn in detail and easily, you may use following references,

  - [LoveIt theme documentation](https://hugoloveit.com/basic-markdown-syntax/)
  - [GRAV documentation](https://learn.getgrav.org/17/content/markdown)

  and of course, there is GitHub wiki. I don't think I need to mention this. 😅
{{< /admonition >}}

# Text formatting

## List
``` markdown
* text
* text
```
* text
* text

``` markdown
    + text
    - text
      - text
      - text
    + text
```
  + text
  - text
    - text
    - text
  + text

{{< admonition >}}
(Above code) +/- doesn't matter here!

For numbered list, it's not this much easy, you've to manually write 1, 2, 3 like this one,
1. hello
2. welcome to my
3. website
{{< /admonition >}}

## Emphasis

``` markdown
***emphasis***
___emphasis___

```
***emphasis***

___emphasis___

## Bold
``` markdown
**bold**
__bold__
```
__bold__

**bold**

## Italic
``` markdown
*italic*
_italic_
```
*italic*

_italic_

## Strikethrough
``` markdown
~~strike~~
```
~~strike~~

## Heading

``` markdown
# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```
## Horizontal lines
``` markdown
---
___
***
```
---
___
***
## Blockquotes
``` markdown
> hello
> this is a Blockquote
>> this is a nested
Blockquote

> Got it?
```
> hello
> this is a Blockquote
>> this is a nested
Blockquote

> Got it?

## Task List
``` markdown
- [ ] this task is incomplete
- [x] this task is completed
```
- [ ] this task is incomplete
- [x] this task is completed

## Inline Code
``` markdown
`code can be in any language` along with text
```
`code can be in any language` along with text

## Indented Code
Indented= putting *some lines* before **a line**, used in *programming*, right? Here we've to use at least 4 space 🧐, though I don't know the reason 😄.
``` markdown
    <pre>
      Yo! This is a test to write
      forward slash = /
      backward slash = \
    </pre>
```
    <pre>
      Yo! This is a test to write
      forward slash = /
      backward slash = \
    </pre>

## Block Fenced Code
``` markdown
    ``` cpp
    #include <iostream>
    int main ()
    {
        std::cout << "Hello world! \nHow cool is that?";
        return 0;
    }
    ```
```
``` cpp
#include <iostream>
int main ()
{
    std::cout << "Hello world! \nHow cool is that?";
    return 0;
}
```
{{< admonition >}}
**Fun Fact ⛱️**

I used `cpp` after first ``` to enable syntax highlighting for c++. Same can be used for javascript (js), markdown (md) or any other languages.
{{< /admonition >}}

## Table

``` markdown
|Left align|Center align|Right align|
| :--- | :---: | ---: |
|Fist column, First row|Second column, First row|Third column, First row|
|First column, Second row|Second column, Second row|Third column, Second row|
|First column, Third row|Second column, Third row|Third column, Third row|
```
|Left align|Center align|Right align|
| :--- | :---: | ---: |
|Fist column, First row|Second column, First row|Third column, First row|
|First column, Second row|Second column, Second row|Third column, Second row|
|First column, Third row|Second column, Third row|Third column, Third row|

{{< admonition >}}
Table without alignment (without using `:`, just `---`) will center align the first row. Second onwards will be using left align!
{{< /admonition >}}

## Links and ancors
``` markdown
<https://t.me/SharafatKarim>
[My telegram](t.me/SharafatKarim)
[My telegram account](t.me/SharafatKarim "My telegram profile")
```
<https://t.me/SharafatKarim>

[My telegram](t.me/SharafatKarim)

[My telegram account](t.me/SharafatKarim "My telegram profile") (Hover over it - desktop PC)

## Table of contents
``` markdown
***Table of Contents***
* [Comment Section](#comments-syntax)
* [Inline Code](#inline-code)
```
***Table of Contents***
* [Comment Section](#comments-syntax)
* [Inline Code](#inline-code)

## Footnotes
``` markdown
This is a footnote [^1]
This is an another footnote with label [^label]

[^1]: This is the note for first footnote
[^label]: This is the note for the second one

```
This is a footnote [^1]

This is an another footnote with label [^label]

[^1]: This is the note for first footnote
[^label]: This is the note for the second one

## Images 🔮
``` markdown
![An octodex image - Fintechtocat](https://octodex.github.com/images/Fintechtocat.png "An octodex image")
```
![An octodex image - Fintechtocat](https://octodex.github.com/images/Fintechtocat.png "An octodex image")

## Comments Syntax
``` markdown
<!-- This is a comment! -->
```
<!-- This is a comment! -->
{{< admonition >}}
Maybe ctrl + / will do the trick 😅

So how will you you view my comment?
- let us know in the comment section 🕹
{{< /admonition >}}
