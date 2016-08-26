---
id: 281
title: 'Mount MS DFS share on linux &#8211; FedoraForum.org'
date: 2010-08-31T08:38:35+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=281
permalink: /281
aktt_notify_twitter:
  - no
categories:
  - Computer
  - Linux
tags:
  - dfs
  - Linux
  - mount
  - windows
---
Install the package “keyutils”:
  
`yum install keyutils`

add these lines to the end of /etc/request-key.conf:
  
`create cifs.spnego * * /usr/sbin/cifs.upcall -c %k<br />
create dns_resolver * * /usr/sbin/cifs.upcall %k`

After that you can mount remote DFS shares as a normal samba share.

via [Mount MS DFS share on linux &#8211; FedoraForum.org](http://forums.fedoraforum.org/showthread.php?t=249327).
