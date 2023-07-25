---
title: "Git Simple Cheatsheet"
date: 2023-06-19T14:26:29+06:00
lastmod: 2023-06-19T14:26:29+06:00
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

# Initializing GIT

## Configuration

1. Name,

 ```bash
 git config --global user.name "Your Name" 
 ```

2. Email,

 ```bash
 git config --global user.email "email@example.com" 
 ```

>📜 "...." - words in this note mean variable. You have to change ‘em!

## Initialization

1. Initialize on a empty directory,

 ```bash
 git init 
 ```

2. Clone from a GitHub/ similar repository,

```bash
 git clone "repo-user/repo-name"
```

3. Clone with all sub-modules,

 ```bash
 git clone --recurse-submodules user/name          
 ```

>  📜  `-j8 ` can be used to boost performance!


4. For an already cloned repository,

 ```bash
 git submodule update --init --recursive 
 ```

## Working with GIT

## Commit  

1. Check status

 ```bash
 git status 
 ```

2. Add a (file|folder) | Work → Stage

 ```bash
 git add "file|folder"
 ```

>  📜 file = file | folder = folder/

 

3. Add everything (except files in the  ```.gitignore ```)

 ```bash
 git add --all 
 ``` 
 or,  
 ```bash
 git add . 
 ```

4. Git commit, | Stage → Commit

 ```bash
 git commit -m "message" 
 ```

5. Git commit with tracked file changes,

 ```bash
 git commit -am "message" 
 ```

>  📜  ```git add . ``` will track untracked files (not ignored) but  ```git add -u ``` won’t!

 

## Reset

1. reset staged changes | Stage → Work

 ```bash
 git reset "file|folder"
 ```

>  📜 or, try  `git reset . ` to reset everything!

 

## Restore

1. restore one file with  
```bash
git restore file/folder            
```
2. restore everything with,
 ```bash
 git restore . 
 ```

## Logging

1. Show the sequence of commits starting from the current one, in reverse chronological order of the Git repository in the current working directory:

 ```bash
 git log 
 ```

2. Show the history of a particular file or directory, including differences:

 ```bash
 git log -p  path/to/file_or_directory  
 ```

3. Show an overview of which file(s) changed in each commit:

 ```bash
 git log --stat 
 ```

4. Show a graph of commits in the current branch using only the first line of each commit message:

 ```bash
 git log --oneline --graph 
 ```

5. Show a graph of all commits, tags and branches in the entire repository:

 ```bash
 git log --oneline --decorate --all --graph 
 ```

6. Show only commits whose messages include a given string (case-insensitively):

 ```bash
 git log -i --grep  search_string  
 ```

7. Show the last N commits from a certain author:

 ```bash
 git log -n  number  --author= author  
 ```

8. Show commits between two dates (  yyyy-mm-dd  ):

 ```bash
 git log --before=" 2017-01-29 " --after=" 2017-01-17 " 
 ```

- Copyright
    
    [https://github.com/tldr-pages/tldr](https://github.com/tldr-pages/tldr)
    

## Sub-module

1. First set it by,

 ```bash
 git submodule add "https://github.com/user/repo-name" "path/"      
 ```

> You can track them from  `.gitmodules` file (a hidden text file) and to sync it’s update with the parent,  `cd ` into it,  `git pull ` and then,  `git add ` in the parent.

## Large file

1. Install    `git-lfs`  first. Available on most of official repository of various Linux distributions.
    
2. set it up (  once per user  ) by running,
 ```git lfs install ```

> make sure file is tracked in the  `.gitattributes` and add it in git. For migrations  `git-lfs-migrate`  
> [This link](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.adoc?utm_source=gitlfs_site&utm_medium=doc_man_migrate_link&utm_campaign=gitlfs) can help you further.

Find more from,

[Git Large File Storage](https://git-lfs.github.com/)

## Remote Branch

1. List all local branches

 ```bash
 git branch 
 ```

>  📜 use  `-r` for remote branches or,  `-a` for all (remote + local)

 
2. New branch

 ```bash
 git branch            branch-name            
 ```

>  📜 Use  ```-M ``` to move a branch, like,  ```git branch -M main ```

 

3. Change branch

 ```bash
 git checkout            branch-name            
 ```

>  📜 Not just branch, you can also trigger a previous commit!

 

4. Deleting a branch

 ```bash
 git branch -D            branch-name            
 ```

## Merge

1. Merge an another branch with the current one,

 ```bash
 git merge           another-branch           
 ```

>  📜 To fix errors, you may need,  ```git merge main --allow-unrelated-histories ```
 

## Sync

1. List all remote,

 ```bash
 git remote -v 
 ```

2. add remote,

 ```bash
 git remote add url    
 ```

3. remove remote,

 ```bash
 git remote remove origin  
 ```

4. push,

 ```bash
 git push -u remote branch        
 ```

>  📜    ```-  e ``` will save       remote       and _      branch      _, for you so next time, just run,  ```git push ```


5. pull,

 ```bash
 git pull 
 ```
