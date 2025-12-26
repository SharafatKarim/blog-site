---
title: "Git Simple Cheatsheet"
date: 2023-06-19T14:26:29+06:00
lastmod: 2025-12-26T09:00:00+06:00
draft: false
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: "Collection of some of the daily driving and most used git commands for easier reference and navigation."
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"
- name: "featured-image-preview"
  src: ""

tags: ['linux', 'git', 'software', 'notes', 'reference']
categories: ['notes']
summary: "Collection of some of the daily driving and most used git commands for easier reference and navigation."

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

# Git Simple Cheatsheet

This is a collection of some of the daily driving and most used git commands for easier reference and navigation.

## Configuration

- Set author name

  ```bash
  git config --global user.name "Your Name"
  ```

- Set author email

  ```bash
  git config --global user.email "email@example.com"
  ```

> 📜 Replace the quoted values with your own.

## Initialization

- Start a new repo in an empty directory

  ```bash
  git init
  ```

- Clone an existing repository

  ```bash
  git clone "repo-user/repo-name"
  ```

- Clone including submodules

  ```bash
  git clone --recurse-submodules user/name
  ```

  > 📜 Add `-j8` to speed up large clones.
- Populate submodules in an already-cloned repo

  ```bash
  git submodule update --init --recursive
  ```

## Staging and Committing

- Check status

  ```bash
  git status
  ```

- Stage specific paths

  ```bash
  git add "file|folder"
  ```

- Stage everything except ignored files

  ```bash
  git add --all
  ```

  or

  ```bash
  git add .
  ```

- Commit staged changes

  ```bash
  git commit -m "message"
  ```

- Commit tracked changes without re-adding

  ```bash
  git commit -am "message"
  ```

  > 📜 `git add .` also picks up new (unignored) files; `git add -u` does not.

## Cleaning

- Drop tracked files that are now ignored (clears stage)

  ```bash
  git rm -r --cached .
  ```

  Then commit; to remove ignored files locally: `git clean -d -x -f`.
- Remove ignored/untracked files locally only

  ```bash
  git clean -d -x -f
  ```

## Reset and Restore

- Unstage changes (Stage → Work)

  ```bash
  git reset "file|folder"
  ```

  > 📜 `git reset .` unstages everything; `git reset --hard` also discards working copy changes.
- Restore one file

  ```bash
  git restore file/folder
  ```

- Restore everything

  ```bash
  git restore .
  ```

## History and Inspection

- Full log

  ```bash
  git log
  ```

- File/directory history with patches

  ```bash
  git log -p path/to/target
  ```

- Commit overview with per-file stats

  ```bash
  git log --stat
  ```

- One-line graph of current branch

  ```bash
  git log --oneline --graph
  ```

- One-line graph of everything

  ```bash
  git log --oneline --decorate --all --graph
  ```

- Search commit messages (case-insensitive)

  ```bash
  git log -i --grep search_string
  ```

- Last N commits by author

  ```bash
  git log -n number --author=author
  ```

- Commits between dates (yyyy-mm-dd)

  ```bash
  git log --before="2017-01-29" --after="2017-01-17"
  ```

## Branches

- List branches (add `-r` for remote, `-a` for all)

  ```bash
  git branch
  ```

- Create a branch

  ```bash
  git branch branch-name
  ```

- Rename current branch

  ```bash
  git branch -M main
  ```

- Switch branches (or checkout a commit)

  ```bash
  git checkout branch-name
  ```

- Delete a branch

  ```bash
  git branch -D branch-name
  ```

## Merging

- Merge another branch into current

  ```bash
  git merge another-branch
  ```

  > 📜 For unrelated histories: `git merge main --allow-unrelated-histories`.
- Prefer current branch changes on conflict

  ```bash
  git merge -s ours another-branch
  ```

- Prefer incoming branch changes on conflict

  ```bash
  git merge -X theirs another-branch
  ```

## Remotes and Sync

- List remotes

  ```bash
  git remote -v
  ```

- Add a remote

  ```bash
  git remote add origin url
  ```

- Remove a remote

  ```bash
  git remote remove origin
  ```

- Push (and set upstream once)

  ```bash
  git push -u remote branch
  ```

  > 📜 After upstream is set, use `git push`.
- Pull latest

  ```bash
  git pull
  ```

## Submodules

- Add a submodule

  ```bash
  git submodule add "https://github.com/user/repo-name" "path/"
  ```

  > Track them in `.gitmodules`; to update, `cd` into the submodule, `git pull`, then stage in the parent.

## Large Files (Git LFS)

- Install Git LFS (once per user)

  ```bash
  git lfs install
  ```

  > Ensure files are tracked in `.gitattributes`; for migrations see `git-lfs-migrate` and the docs below.
- Docs: [Git Large File Storage](https://git-lfs.github.com/)

## Authentication (GitHub)

You can simply use `github-cli` to authenticate with GitHub. Install it, and run,

```bash
gh auth login
```

## Signing Commits (GPG)

To sign commits, and send signed tags, you need to have GPG installed and configured. Follow this guide,

- <https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key>

To sign all commits by default,

```bash
git config --global commit.gpgSign true
```

## Troubleshooting

- Handy reference when things go sideways: [Oh Shit, Git!?!](https://ohshitgit.com/)

## Acknowledgements

- Copyright: [https://github.com/tldr-pages/tldr](https://github.com/tldr-pages/tldr)
