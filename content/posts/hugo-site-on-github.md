---
title: "Hugo Site on Github"
date: 2020-11-11T06:25:58+01:00
draft: false
description: "How to use Hugo to generate a static site"
tags: ["Development","Hugo", "Git"]
---

References:
* [Hugo site](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
* [Hugo quickstart](https://gohugo.io/getting-started/quick-start/)


## Install Hugo and bootstrap site folder

First we need to install `hugo` with `brew install hugo`.

Then create the site/folder:

``` bash
hugo new site blog
cd blog
git init
```

Choose a [Theme](https://themes.gohugo.io/) and install it as git submodule

``` bash
git submodule add https://github.com/panr/hugo-theme-hello-friend.git themes/hello-friend
```

Then do a first commit and push to a new empty repository on github

``` bash
git add .
git commit -m"Initial commit"
git remote add origin https://github.com/tgarlot/blog.git
git push -u origin master
```

## Create some content

Create some content (like a new post)

``` bash
hugo new posts/new-post.md
```

Then add, commit and push the changes.

## Publish

First create a new repository on Github that will content the generated HTML content of the site. It MUSt be named _username_.github.io

Generate site  with `hugo` command. It will output files into the `public` folder. Initialise a Git repo and commit the generated files.

``` bash
hugo
cd public
git init
git add .
git commit -m"Initial commit"
```
Add a remote to the Github repository and push.

``` bash
git remote add origin https://github.com/tgarlot/tgarlot.github.io.git
git push -u origin master
```

Then add the `public` as a Git submodule:

``` bash
cd ..
rm -rf public
git submodule add -b master https://github.com/tgarlot/tgarlot.github.io.git public
git add .
git commit -m"Add public folder as submodule"
git push -u origin master
```
## Add or edit some content

* update a markdown file
* run hugo command to regenerate the content of the public folder
* add/commit/push in BOTH repositoriy (public and content)
