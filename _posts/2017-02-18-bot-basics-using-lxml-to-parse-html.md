---
title: "Bot basics: using lxml library to parse HTML"
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - lxml
  - html
  - python
---

In a recent and ongoing project, I needed bot to collect some public data from
Internet for analysis. One basic function a bot would perform, other than
sending HTTP requests and receiving responses, is of course parsing the
responses and finding out data of interest. In many if not most cases, the HTTP
response would be in HTML format; therefore, a bot who understands HTML is
warranted and so is a library to parse HTML.

As I've become comfortable with Python in the past couple years, I certainly
started looking at what's available for Python, and there I found [`lxml`](http://lxml.de/):

> lxml is the most feature-rich and easy-to-use library for processing XML and
> HTML in the Python language.

The power of `lxml` comes from `libxml2` and `libxslt`, as explained by the
Introduction section of its [homepage](http://lxml.de/):

> The lxml XML toolkit is a Pythonic binding for the C libraries libxml2 and
> libxslt. It is unique in that it combines the speed and XML feature
> completeness of these libraries with the simplicity of a native Python API,
> mostly compatible but superior to the well-known ElementTree API.

Sounds pretty awesome, doesn't it? Below please allow me to walk you through an
quick example so you could get a peek of how useful `lxml` is when processing
HTML.

Let's say the HTML has a table nested deep-down but containing the data the bot
wants to extract, for example,

    <html>
    ...
    <div>
        <div>
            ...
            <table>
                <tr class="a-nice-tr-class">
                    <td class="alex-says">Good morning</td>
                    <td class="mike-says">Good afternoon</td>
                    <td class="me-cry">Good bye</td>
                </tr>
                <tr class="a-nice-tr-class">
                    <td class="alex-says">Oh yeah!</td>
                    <td class="mike-says">Oh no!</td>
                    <td class="me-cry">Uh-oh</td>
                </tr>
                ...
            </table>
        </div>
    </div>
    </html>

