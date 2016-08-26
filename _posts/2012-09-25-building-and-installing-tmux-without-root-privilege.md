---
id: 392
title: Building and installing tmux without root privilege
date: 2012-09-25T21:54:20+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=392
permalink: /392
categories:
  - Linux
tags:
  - Linux
  - tmux
---

1. Get libevent source from [libevent.org](libevent.org) and build. This will
install the header files and libraries under folder `$HOME/local`

2. Get tmux source from [tmux.sourceforge.net](tmux.sourceforge.net) and build.
This will statically link to libevent and put the binary under folder
`$HOME/local`

3. Add `$HOME/local/bin` to your `PATH` and tmux is ready to rock.
