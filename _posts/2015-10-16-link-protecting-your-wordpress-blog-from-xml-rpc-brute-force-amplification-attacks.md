---
id: 500
title: 'Link: Protecting Your WordPress Blog From XML-RPC Brute Force Amplification Attacks'
date: 2015-10-16T23:43:38+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=500
permalink: /500
categories:
  - Computer
tags:
  - security
  - wordpress
---

From [Protecting Your WordPress Blog From XML-RPC Brute Force Amplification
Attacks](https://pop.co/blog/protecting-your-wordpress-blog-from-xmlrpc-brute-force-amplification-attacks/):

> To summarize, attackers are taking advantage of a vulnerability in
> WordPress’s XML-RPC system.multicall method which effectively allows them to
> issue hundreds of login attempts with a single request. To put it another
> way, this is an extreme case of brute forcing logins in an attempt to
> determine your administrative user credentials.

Validate the change as suggested from a comment of the above link (xml-rpc
should be disabled):

> You can check if XML-RPC is enabled on your site with [this tool](http://xmlrpc.eritreo.it/)
