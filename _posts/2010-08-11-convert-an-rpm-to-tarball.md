---
id: 274
title: Convert a RPM package to tarball
date: 2010-08-11T10:41:56+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=274
permalink: /274
aktt_notify_twitter:
  - no
categories:
  - Computer
tags:
  - Linux
  - rpm
  - tarball
---
This might be a weired use case, but sometime one may want to extract all contents from an RPM and neatly put into a tarball.

If you are still reading, here comes the shell script to do the task.

<pre>#!/bin/sh

EXEC="=== "`basename $0`
PWD=`pwd`
RPMFILE=`readlink -f $1`

if [ -z "$2" ]; then
        TGZFILE=$PWD/`basename $1 | sed 's/rpm/tgz/g'`
else
        TGZFILE=$2
fi
TMPDIR=/tmp/$0-`whoami`

rm -rf $TMPDIR
mkdir -p $TMPDIR

echo "$EXEC: Changing to TMPDIR=$TMPDIR"
cd $TMPDIR

echo "$EXEC: Unpacking RPMFILE=$RPMFILE"
rpm2cpio $RPMFILE |cpio -idmv

echo "$EXEC: Generating zipped tarball TGZFILE=$TGZFILE"
tar -zcvf $TGZFILE *

echo "$EXEC: Done"</pre>

Sure there are many ways to improve, e.g., include a usage, but it&#8217;s working fine for me as it is.
