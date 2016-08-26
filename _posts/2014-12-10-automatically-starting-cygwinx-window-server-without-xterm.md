---
id: 469
title: Automatically starting Cygwin/X Window Server without xterm.
date: 2014-12-10T17:48:48+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=469
permalink: /469
categories:
  - Computer
tags:
  - cygwin
  - xorg
format: quote
---
From [True Blade](http://www.trueblade.com/knowledge/automatically-starting-a-cygwin-x-server):

> To start the cygwin X server, create a new shortcut in your Startup group. It should execute this command:
  
> `<path-to-cygwin>\bin\run.exe -p /usr/X11R6/bin XWin -multiwindow -clipboard -silent-dup-error`
  
> For my setup, where I have cygwin installed in c:\opt\cygwin, the entire command is:
  
> `C:\opt\cygwin\bin\run.exe -p /usr/X11R6/bin XWin -multiwindow -clipboard -silent-dup-error`
  
> Now, whenever I log in to Windows, the X server automatically starts, and I don&#8217;t have any annoying text windows that I might accidentally close.
