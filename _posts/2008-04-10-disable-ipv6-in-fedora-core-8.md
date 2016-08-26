---
id: 28
title: Disable IPv6 in Fedora Core 8
date: 2008-04-10T15:09:56+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=28
permalink: /28
categories:
  - Computer
  - Linux
  - Networking
tags:
  - fedora core
  - Linux
  - networks
---
Almost no pre-existing instructions on this issue works on Fedora Core 8.

Now here is how you can do this with FC8 to disable IPv6:

1. Append the following line to `/etc/modprobe.conf`:

        install ipv6 /bin/true

2. Append the following line to `/etc/sysconfig/network`:

        NETWORKING_IPV6=no

3. Ensure your network adapter is configured not to use IPv6. This is an easy
edit in the `system-config-network` gui, or do it manually in
`/etc/sysconfig/network-scripts/ifcfg-eth0` (ammend for name of your adapter)
by appending

        IPV6INIT=no

