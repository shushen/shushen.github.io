---
id: 35
title: Using yum-fastestmirror to speed up your Fedora software package updates
date: 2008-06-16T15:42:07+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=35
permalink: /35
categories:
  - Linux
tags:
  - fedora core
  - Linux
---
The package manager, `yum`, on Fedora uses a [mirror management infrastructure](http://fedoraproject.org/wiki/Infrastructure/MirrorManagement) to help locate the geographically closest mirrors. This &#8220;geographically closest&#8221; mirror is supposed to give you the fastest connection &#8211; which unfortunately is usually not the case. For example, the connection between Mainland China and Taiwan is extremely slow despite it&#8217;s geographical neighborhood.

Therefore, the `yum-fastestmirror` plugin becomes very helpful. Quote from [Fedora documentation](http://fedoraproject.org/wiki/Docs/Drafts/SoftwareManagementGuide/CustomizingYum#Fastest_Mirror_Plugin)

> The fastest mirror plugin enhances the speed of updates by maintaining a local offline hostfile cache of the speed of the mirrors. It sorts the mirror list by speed and prioritizes the faster ones for package downloads.

Enter the command to install:
  
`su -c 'yum install yum-fastestmirror'`

One may exclude certain domains from even being listed at all by adding the following line to `/etc/yum/pluginconf.d/fastestmirror.conf`:
  
`exclude=.tw, .jp`

Then you&#8217;re up to the speed &#8230; Have fun!
