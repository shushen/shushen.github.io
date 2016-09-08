---
title: Switched to jekyll and CloudFlare
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - https
  - wordpress
  - jekyll
  - cloudflare
---

[Dreamhost]( https://www.dreamhost.com) has been a great host for many years
but there are other options for hosting a plain blog like this one these days,
which makes paying out ~$50 for two years' hosting start feeling too much.

So I finally converted to
[jekyll](https://jekyllrb.com)+[github-pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)
solution and uses a free plan from [CloudFlare](https://www.cloudflare.com) to
front the blog with HTTPS. In order to do its job, CloudFlare also becomes my
domain DNS server.

CloudFlare for this site now runs in Full SSL mode, which means SSL is run
between visitors and CloudFlare CDN, as well as between CloudFlare and
github-pages.

I cannot run Full (strict) mode, which would ask CloudFlare to validate its
connection to github-pages with a server-side certificate for my domain,
because github-pages only serve HTTPS with a certificate for
github.com/github.io.
