---
id: 509
title: Switched to HTTPS/TLS
date: 2016-03-16T05:36:08+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=509
permalink: /509
categories:
  - Computer
  - Networking
tags:
  - https
  - wordpress
---

Thanks to [Dreamhost](
https://www.dreamhost.com/blog/2015/12/03/lets-encrypt-and-dreamhost/) and
[Let's Encrypt](https://letsencrypt.org), this WordPress site is now serving
over HTTPS only.

Switching to HTTPS with Dreamhost and Let's Encrypt was pretty
straightforward and took about 1 hour or so at most, thanks to the nice guide
by
[Aaron](https://aarontgrogg.com/blog/2015/12/11/adding-https-to-my-dreamhost-wordpress-site/).
I didn't see some of the trouble with PHP - it might well be the
case that Dreamhost has updated their default PHP configuration for hosted
sites.

The procedure I took was:

1. Update WordPress and all plugins to latest.
1. Backup your database
1. Enable "Secure Hosting" on Dreamhost Panel
1. Put .htaccess with the excellent permanent redirect from http to https by
Aaron:

        <IfModule mod_rewrite.c>
        # enable Rewrite
        RewriteEngine On
        # make sure not already HTTPS
        RewriteCond %{HTTPS} !=on
        # redirect from original to same location using HTTPS
        RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R=301,L]
        </IfModule>

1. Clean up database by replacing all local refs to use HTTPS using the SQL
presented by Aaron (replace `domainname` with your own):

        UPDATE wp_comments SET comment_author_url = replace(comment_author_url, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_comments SET comment_content = replace(comment_content, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_options SET option_value = replace(option_value, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_postmeta SET meta_value = replace(meta_value, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_posts SET post_content = replace(post_content, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_posts SET guid = replace(guid, 'http://domainname.com', 'https://domainname.com');
        UPDATE wp_sitemeta SET meta_value = replace(meta_value, 'http://domainname.com', 'https://domainname.com');

1. If possible update external references with HTTPS as well (e.g., [serving
Google fonts over
HTTPS/HTTP](http://www.amixa.com/blog/2012/06/06/how-to-use-google-fonts-under-both-ssl-and-non-ssl-without-ssl-insecure-messages/))
