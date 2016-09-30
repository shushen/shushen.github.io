---
title: Running docker with docker-machine and xhyve on macOS
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - docker-machine
  - docker
  - macos
  - xhyve
  - containers
---

[xhyve](https://github.com/mist64/xhyve) is a lightweight OS X virtualization
solution and can run on OS X 10.10 Yosemite and higher. xhyve currently
supports FreeBSD and Linux distributions as guest systems. xhyve also has a
[docker-machine driver](https://github.com/zchee/docker-machine-driver-xhyve)
that allows you to use [docker-machine](https://github.com/docker/machine) to
run docker containers in side a VM and easily manage the lifecycle of the
docker container and the VM.

These three components combined is a nice lightweight docker solution on macOS,
and all of them can be installed and updated by [Homebrew](http://brew.sh).  It
is a much better fit with a developer's console-based workflow - No more
VirtualBox and its annoying updates!

Assuming you've already have Homebrew installed, here is how to install xhyve
and docker-machine-driver-xhyve:

    $ brew update
    $ brew install --HEAD xhyve
    $ brew install docker-machine-driver-xhyve

The last command will also install docker-machine as a dependency.

Then make sure you change the docker-machine-driver-xhyve binary for proper
permissions (due to Homebrew policy this could not be automated):

    $ sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
    $ sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve

Now that you have everything installed, start a helloworld docker:

    $ docker-machine create -d xhyve helloworld

Tested with the following software versions:

 - macOS 10.12 (16A323)
 - Homebrew 1.0.5
 - xhyve: stable 0.2.0
 - docker-machine: stable 0.8.2
 - docker-machine-driver-xhyve: stable 0.2.3
