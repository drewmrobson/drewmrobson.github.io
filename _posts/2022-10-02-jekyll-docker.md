---
layout: post
title:  "Custom CSS in Jekyll in Docker in 2022"
date:   2022-10-02 00:00:00 +1000
categories: build
tags: build
excerpt_separator: <!--more-->
---
This blog is built with [Jekyll](https://jekyllrb.com/) (a static site generator) and [GitHub Pages](https://pages.github.com/) (a static site host which supports Jekyll). It was frustrating learning how to run a Jekyll development environment and customise the site css, so I've provided a short guide with the aim to save others the pain.

<!--more-->

## Get these tools

- [VSCode](https://code.visualstudio.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

## Then do this

Open a Git Bash terminal in VSCode

![picture 1](/assets/images/876bea6362b0d48783dab744b26c892ef72dfae6f677487ea0a88e106a9cf138.png)  

Execute this command

```bash
cd C:/Source/my-folder
```

Then these commands

```bash
docker pull jekyll/builder:4.2.0
export site_name="my-blog" && export MSYS_NO_PATHCONV=1
docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/builder sh -c "chown -R jekyll /usr/gem/ && jekyll new $site_name" && cd $site_name
```

Now you have a Jekyll site ready to be built. Before we do this, let's customise the css. Run these commands

```bash
mkdir assets
cd assets
touch main.scss
cd ..
```

Add this style override to `main.scss`

```sass
---
---

@import "minima";

h1 {
    color: red;
}
```

Then run these commands to build and run a local server

```bash
docker run --rm --volume="$PWD:/srv/jekyll:Z" jekyll/builder:4.2.0 jekyll build
docker run --rm --volume="$PWD:/srv/jekyll:Z" --publish 7333:7333 jekyll/builder:4.2.0 jekyll serve --host 0.0.0.0 --port 7333
```

Go to `http://localhost:7333/jekyll/update/2022/09/29/welcome-to-jekyll.html` and you'll see the title is now red.

![picture 3](/assets/images/9a2b511375173d520bc99366b615939d9cafefbc3f711b70b00130f28b45376f.png)  

I hope that helps someone quickly get their Jekyll blog up and running in their local development environment quickly.