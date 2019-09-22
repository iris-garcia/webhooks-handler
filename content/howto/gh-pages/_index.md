+++
title = "GitHub Pages"
author = ["Iris Garcia"]
lastmod = 2019-09-22T13:22:52+02:00
tags = ["ci", "hugo", "doc"]
draft = false
weight = 1
asciinema = true
+++

This document ilustrates how to setup [GitHub Pages](https://pages.github.com/) using [Hugo](https://gohugo.io/) as
website generator and [GitHub's Actions](https://github.com/features/actions) to automate the deployment
process.

There are different alternatives to setup GitHub pages, the one used
in here is a project pages using `gh-pages` branch, the advantages
are:

-   It keeps your source and generated website in different branches and
    therefore maintains version control history for both.
-   It uses the default Hugo's **public** folder.

So basically this project's repository has the following branches:

-   **master**: Hosts the source code of the project.
-   **hugo**: Hosts the source code of the documentation website.
-   **gh-pages**: Hosts the static assets generates by hugo.


## Step 1: Initializing branches {#step-1-initializing-branches}

```bash
# Hugo branch
git checkout -b hugo
echo "public" >> .gitignore
git add .gitignore
git commit -m "Adds .gitignore"
hugo new site .
git add .
git commit -m "Adds initial hugo site"
git push origin hugo

# gh-pages branch
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "Initializing gh-pages branch"
git push origin gh-pages
```


## Step 2: Adding GitHub's action {#step-2-adding-github-s-action}
