---
layout: post
title:  "Custom CSS in Jekyll in Docker in 2022"
date:   2022-10-02 00:00:00 +1000
categories: build
excerpt_separator: <!--more-->
---
This blog is built with [Jekyll]() and [GitHub Pages](). It was frustrating learning how to run a Jekyll development environment and customise the site css, so I've provided a short guide with the aim to save others the pain.

<!--more-->
More

```bash
docker pull jekyll/builder:4.2.0
export site_name="my-blog" && export MSYS_NO_PATHCONV=1
docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/builder sh -c "chown -R jekyll /usr/gem/ && jekyll new $site_name" && cd $site_name
docker run --rm --volume="$PWD:/srv/jekyll:Z" jekyll/builder:4.2.0 jekyll build
docker run --rm --volume="$PWD:/srv/jekyll:Z" --publish 7333:7333 jekyll/builder:4.2.0 jekyll serve --host 0.0.0.0 --port 7333
```