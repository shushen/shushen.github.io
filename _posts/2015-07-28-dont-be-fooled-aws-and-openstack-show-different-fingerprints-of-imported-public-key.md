---
id: 472
title: 'Don&#8217;t Be Fooled! AWS and Openstack Show Different Fingerprints of Imported Public Key'
date: 2015-07-28T23:58:54+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=472
permalink: /472
categories:
  - Computer
tags:
  - aws
  - openstack
---
Don&#8217;t be fooled! AWS and Openstack are fingerprinting an imported keypair differently.

AWS uses the equivalent of:

`openssl rsa -in id_rsa -pubout -outform DER | openssl md5 -c`

while Openstack uses ssh-keygen:

`ssh-keygen -q -l -f id_rsa`

They could end up showing different values for the fingerprint of exactly the same public key.

References:
  
[1] AWS: <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#verify-key-pair-fingerprints>
  
[2] Openstack: <https://github.com/openstack/nova/blob/master/nova/crypto.py#L133>
