---
id: 242
title: How To Extract files from an RPM Package Without Installing It
date: 2010-04-29T10:10:44+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=242
permalink: /242
aktt_notify_twitter:
  - no
categories:
  - Computer
tags:
  - Linux
  - rpm
---
Extract RPM file using rpm2cpio and cpio command:
  
`$ rpm2cpio php-5.1.4-1.esp1.x86_64.rpm | cpio -idmv` 

via [How To Extract an RPM Package Without Installing It rpm extract command](http://www.cyberciti.biz/tips/how-to-extract-an-rpm-package-without-installing-it.html).
