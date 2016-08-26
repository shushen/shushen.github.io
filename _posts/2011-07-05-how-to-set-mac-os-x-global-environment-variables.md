---
id: 373
title: How to set Mac OS X Global Environment Variables
date: 2011-07-05T03:29:58+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=373
permalink: /373
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
categories:
  - Computer
  - Mac
tags:
  - mac
---
I have recently switched to MacBook Air and started exploring the fantastic Mac
OS X - a pleasant OS on a pleasant piece of hardware.

This week I'm trying out setting up a LISP environment with Clozure CL and
Emacs/SLIME. I'm using the [Emacs for Mac OS](http://emacsformacosx.com/) and
SLIME. I needs tell a LISP script about where to find the LISP installation
with the environment variable CCL\_DEFAULT\_DIRECTORY. It's rather easy to do
this for consoles - but how to do it with Emacs.app, the cocoa-version?

There has been some searching on Google and it turns out the following works
perfect: edit /etc/launchd.conf to contain a line like this:

> setenv M2_HOME /opt/maven/2.0.9

<del datetime="2011-07-07T11:39:10+00:00">Note that one can also do this with
~/.launchd.conf, which only affects the user only.</del> The per user
.launchd.conf does not seem working - I lost the configuration once I restarted
- it worked only because I used the below command to pipe the configuration
into launchctl.

It's also possible to take the changes into effect without rebooting or even
logging out by

    grep ^setenv ~/.launchd.conf | launchctl

via [Mac OS X Global Environment Variables \| Digital Edge Software and
Consulting](http://www.digitaledgesw.com/node/31).
