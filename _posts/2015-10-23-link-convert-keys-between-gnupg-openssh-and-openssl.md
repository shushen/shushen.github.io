---
id: 502
title: 'Link: Convert keys between GnuPG, OpenSsh and OpenSSL'
date: 2015-10-23T20:58:50+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=502
permalink: /502
categories:
  - Computer
  - Linux
tags:
  - keys
  - openssl
  - ssh
---

From [Convert keys between GnuPG, OpenSsh and
OpenSSL](http://www.sysmic.org/dotclear/index.php?post/2010/03/24/Convert-keys-betweens-GnuPG%2C-OpenSsh-and-OpenSSL):

> OpenSSL to OpenSSH
> 
> Private keys format is same between OpenSSL and OpenSSH. So you just a have
> to rename your OpenSSL key:
> 
>       cp myid.key id_rsa
> 
> In OpenSSL, there is no specific file for public key (public keys are
> generally embeded in certificates). However, you extract public key from
> private key file:
> 
>       ssh-keygen -y -f  myid.key > id_rsa.pub

[Update] Also converting from OpenSSH private key to .pem in X.509 format,
which is a format required by [Microsoft Azure
VMs](http://[https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-use-ssh-key/]):

>       openssl req -x509 -key ~/.ssh/id_rsa -nodes -days 365 -newkey rsa:2048 -out myCert.pem
