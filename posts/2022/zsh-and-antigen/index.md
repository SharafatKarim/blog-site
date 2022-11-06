---
title: "zsh and antigen - installation to customization"
date: 2022-10-30T08:41:37+06:00
lastmod: 2022-10-30T08:41:37+06:00
draft: false
author: ""
authorLink: ""
description: "A guide to install and customize zsh along with different plugins with the help of antigen plugin manager."
license: ""
images: []

tags: ["linux","zsh","tutorial"]
categories: ["linux"]
summary: "A guide to install and customize zsh along with different plugins with the help of antigen plugin manager."

featuredImage: "featured-image.png"
featuredImagePreview: "featured-image-preview.png"

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

A guide to install and customize zsh along with different plugins with the help of antigen plugin manager. But what are those?

## ZSH and Antigen

> ZSH
>> The Z shell! A Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting.

> Antigen
>> Yet, an another plugin manager for zsh!

---

Antigen's official [docs](https://github.com/zsh-users/antigen) says,

{{< typeit >}}
*Antigen is a small set of functions that help you easily manage your shell (zsh) plugins, called bundles*
{{< /typeit >}}

---

## Why zsh?
Why? We've bash, right? Well, you can extend it's features more easily along with awesome customizations! Do you need anything else?

---

Z shell's official [website](https://www.zsh.org/) says,

{{< typeit >}}
*Zsh is a shell designed for interactive use, although it is also a powerful scripting language. More information can be found on the "Zsh Web Pages" sites.*
{{< /typeit >}}

---

Still confused? Well, just try once, if you don't like it you can always revert back 😆.

## Why antigen?
We've got a lot of popular zsh plug-in managers like oh-my-zsh, zplug and so on. So why antigen?
- It's fast ✨

{{< admonition note "Well," true >}}
How do I know it's faster or slower? Check benchmarks from [here](https://github.com/rossmacarthur/zsh-plugin-manager-benchmark) 😅.
And if you don't believe this benchmark then run it for yourself. If you notice a significance change then tell that [ Avatar crab Ross MacArthur](https://github.com/rossmacarthur), not me 🫠.
{{< /admonition >}}

And I think it's more easier. 🎯

## Installing zsh

You can most probably install right from your operating system's official package manager.
Alternatively, you can check [this list](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH#how-to-install-zsh-on-many-platforms), if you need help installing zsh.

To make sure zsh is installed, fire up your terminal and execute,

```bash
zsh --version
```

## Default shell

Whenever you fire up your terminal, do you find zsh? If yes, then `zsh` is your default shell. Alternatively, run the following command,

```bash
echo $SHELL
```

If your output is `/bin/zsh` or `/usr/bin/zsh` then, zsh is your default shell.

So how do you make zsh your default?
run the following command,

```bash
chsh -s $(which zsh)
```

Don't have the admin privilege? Check [this thread](https://unix.stackexchange.com/questions/136423/making-zsh-default-shell-without-root-access) then.

{{< admonition warning "And, also" >}}
don't forget to re-login (log out and log in) to change effect. Don't I need to restart 🧐?

We don't do that here 😅
{{< /admonition >}}


## Antigen Installation
### Installation

No big deal, just run the following command,

{{< typeit code=bash >}}
curl -L git.io/antigen > antigen.zsh
{{< /typeit >}}

---

What will this command do? 🧐

Go to your home directory(`/home/$USER/`), you'll find a new file, named `antigen.zsh`. We've no business with this file, so let's forget, it exists in our system 😆.

---

Believe it or not, antigen is now installed 😅. Now we just have to modify `.zshrc` file in our home directory. Everything will depend on it! ✨

### zshrc file

{{< admonition info "What is .zshrc file?" true >}}
This is the file associated with ZSH. It exists on your home directory and it's a hidden file because it's name starts with a dot/ period (` . `).

Go to your home directory and look for this file. To show hidden files you have to enable it. Default shortcut is `ctrl + h`, I think 🧐. And if you're using terminal, then you've got `ls -a` command. 😅

If this file doesn't exit then open a terminal and if zsh is your default shell then you'll be prompted with something strange 😅. No need to worry, just press 0 or skip that part. Cause we're gonna destroy it later 👿.
{{< /admonition >}}


---

Now open `.zshrc` file with our favorite text editor, and prepare for the worst 🎃.

Copy the following lines to your `.zshrc` file,

```bash
source ~/antigen.zsh

# Load the oh-my-zsh's library.
antigen use oh-my-zsh

# Bundles from the default repo (robbyrussell's oh-my-zsh).
antigen bundle git
antigen bundle heroku
antigen bundle pip
antigen bundle lein
antigen bundle command-not-found

# Syntax highlighting bundle.
antigen bundle zsh-users/zsh-syntax-highlighting

# Load the theme.
antigen theme robbyrussell

# Tell Antigen that you're done.
antigen apply
```

## Antigen Usage
### understanding zshrc

To make it simple, let's say whenever you fire up your terminal, whatever zshrc contains will be executed. How kool is that?

---

That means whatever we've added to our `.zshrc` will also be executed?
- yes

And can we run those lines without using `.zshrc`?
- yes 👿.
But make sure to run `source ~/antigen.zsh` first. Cause, you know, we've installed our antigen to `antigen.zsh`.

---

### understanding antigen

Now it's time, let's see what've done so far in `.zshrc`. We've first used this line to show him the location of antigen.
```bash
source ~/antigen.zsh
```

Then, we've loaded [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) library (the most popular one for zsh).
```bash
antigen use oh-my-zsh
```

{{< admonition warning "Another thing," true >}}
I'm not telling you to run above command! It's inside of your `.zshrc` file. But yeah! You can run it for sure. It'll work until you close your current terminal/ session. In this way you can check a command before putting into `.zshrc`.
{{< /admonition >}}

As we've oh-my-zsh now on our hands, who can tell us to stop 😅? Now we can easily load oh-my-zsh bundles using commands like,

```bash
antigen bundle git
antigen bundle heroku
antigen bundle pip
antigen bundle lein
antigen bundle command-not-found
```

And let's not forget oh-my-zsh themes. In the above example (.zshrc) we've used `robbyrussell`. And you can change it for sure! check,
- [oh-my-zsh themes collection that you can use directly](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)

Let's say, you want to install the theme, named [refined](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#refined). Then you can modify the `.zshrc` file and set theme to `refined`.
```bash
# Load the theme.
antigen theme refined
```

## Plugin installation

Now you may want to install custom antigen plugins from various GitHub repositories. And if you don't know what to install, here's a list you can try,
- [awesome zsh plugins](https://github.com/unixorn/awesome-zsh-plugins)

---
### zsh auto notify

For now let's install two most common and interesting plugins! First one is `zsh-auto-notify`. Whenever a long process is finished you will get a notification through `notify-send`. Check it's repository,
- [ZSH auto notify](https://github.com/MichaelAquilina/zsh-auto-notify)

Now how can we install it? Simple! Check the URL of GitHub of this repository. It's,

https://github.com/MichaelAquilina/zsh-auto-notify

We've to collect the `username/repository-name`. For this case it's `MichaelAquilina/zsh-auto-notify`.  Then to install it we have to put the following line to our `.zshrc`,
```bash
antigen bundle MichaelAquilina/zsh-auto-notify
```

---
### zsh-autosuggestions

Similarly let's install one more called `zsh-autosuggestions`. It's repository's link is,

https://github.com/zsh-users/zsh-autosuggestions

So, to install we've to use,
```bash
antigen bundle zsh-users/zsh-autosuggestions
```

### Repo with different branch

Did you notice the branch name from GitHub for above two commands. It's ***master***, right?

If your branch isn't master, then our command will be little different.

Suppose the branch is `main` then the command will be like,
```bash
antigen bundle github-user/repo --branch=main
```

{{< admonition warning "Another thing," true >}}
Above command is an example. Don't run it, or it'll throw you an error. Suppose in future you fail to install any plugin for errors like,

`Error! Activate logging and try again.`

Then be sure to check the branch name of that repository.
{{< /admonition >}}

## Optimization and plugin settings

Let's say you've installed some plugins to test and then you decided not to use them. So you removed them from `.zshrc`. But the files?

Did you notice there's a folder in your home directory now called `.antigen`? This is where all of your plugin exits. If this folder or directory doesn't exist then whenever you'll fire up the terminal, it'll be automatically be created. So what'll you do to optimize your space?
- Just delete the directory 🫠.

{{< admonition note "BTW," true >}}
If you do regularly backup your dotfiles from your home directory, you don't need to track or backup, that `.antigen` directory(unless you customize plugins). Just avoid it! It'll be created automatically, as long as `antigen.zsh` exits and your zshrc knows how to use antigen! 🎃
{{< /admonition >}}

Now, what about the plugin settings?
- Discover the `.antigen` directory and you'll find corresponding plugins. And then I think you can follow along their official documentations!

## Uninstallation

To uninstall ZSH, uninstall from your package manager. Then what about antigen? Here antigen isn't a package. So you can just go to your home directory and remove `.antigen` directory, `.zshrc` and other zsh stuff and finally `antigen.zsh`.

## Wrapping up

Now I think, you've successfully installed antigen and zsh with a good looking theme. If you've messed up or couldn't follow along, here's my `.zshrc` after this tutorial.

```bash
source ~/antigen.zsh

# Load the oh-my-zsh's library.
antigen use oh-my-zsh

# Bundles from the default repo (robbyrussell's oh-my-zsh).
antigen bundle git
# antigen bundle heroku
antigen bundle pip
# antigen bundle lein
antigen bundle command-not-found

# Syntax highlighting bundle.
antigen bundle zsh-users/zsh-syntax-highlighting

# Load the theme.
antigen theme refined

antigen bundle MichaelAquilina/zsh-auto-notify
antigen bundle zsh-users/zsh-autosuggestions

# Tell Antigen that you're done.
antigen apply
```
If you've any questions or queries or any doubt, feel free to contact me or maybe [our telegram group](t.me/LinuxUniverse) 😅. And if you don't like ZSH there is also [fish](https://fishshell.com/). Maybe I'll write another one for fish, who knows? 😆

Thanks for reading this far.

{{< admonition quote "TO-DO" true >}}
- [ ] List useful ZSH plugins
- [ ] List useful `alias` for zsh

I'll really appreciate your help
{{< /admonition >}}
