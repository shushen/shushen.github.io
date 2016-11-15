---
title: Import qcow2 images into AWS
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - amazon
  - aws
  - ami
  - snapshot
  - qemu
  - qcow2
  - cloud
  - iaas
---

When running multi-cloud applications, sometimes you may want to move an disk
image or snapshot from a [qemu](http://wiki.qemu.org/)-based virtualization
environment into a public cloud such as [Amazon Web Services
(AWS)](https://aws.amazon.com).

[qcow2](http://wiki.qemu.org/download/qemu-doc.html#disk_005fimages_005fformats)
is the most common and also the native format of the disk image used by qmeu.
Unfortunately, qcow2 is not a format that the AWS `import-image` tool can
import directly - the tool only supports VMDK, VHD, and RAW formats at the time
of writing. Therefore, additional steps need be taken to convert the image from
`qcow2` into `raw` for AWS to import.

The rest of this post describes how to import qcow2 images into AWS as a
snapshot. Once the image is imported as a snapshot, an Amazon Machine Image
(AMI) could be created from the snapshot and used to launch new instances.
This procedure requires a Linux host running Ubuntu and access to [AWS S3
service](https://aws.amazon.com/s3/). The Linux host would be preferably
running on AWS for faster data transfer to and from S3.

* Prerequisites:
    * Assume the QCOW2 image to be converted/imported is located at
      `~/example.qcow2`
    * The Linux host shall have enough disk space to hold the expanded RAW
      image, which would be as large as the `virtual size` of the image (see
      step 2 below for how to find out the `virtual size` of an image).

1. Install `qemu-utils` package to get the `qemu-img` tool

        $ sudo apt-get install qemu-utils

2. Find out the `virtual size` of the disk image and ensure you have enough
   space to hold the expanded RAW image:

        $ qemu-img info example.qcow2
        image: example.qcow2
        file format: qcow2
        virtual size: 39M (41126400 bytes)
        disk size: 13M
        ...

3. Use `qemu-img` to convert the image into RAW format. The expanded RAW image
is about 39M for this specific image

        $ qemu-img convert example.qcow2 example.raw

4. Install AWS CLI:

        $ sudo pip install awscli --ignore-installed six

5. Put your AWS credentials under `~/.aws/config`, see [AWS
CLI configuration reference](http://docs.aws.amazon.com/cli/latest/topic/config-vars.html) for
details

        [default]
        aws_access_key_id=FOO
        aws_secret_access_key=BAR

6. Copy the RAW image into S3, assume you've already had an S3 bucket named `raw-images`

        $ aws s3 cp example.raw s3://raw-images

7. Create `vmimport` role and assign proper policy for the S3 bucket by
following the AWS procedure
[here](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/VMImportPrerequisites.html#vmimport-iam-permissions):

        $ vim trust-policy.json
        $ aws iam create-role --role-name vmimport --assume-role-policy-document file://trust-policy.json
        $ vim role-policy.json
        $ aws iam put-role-policy --role-name vmimport --policy-name vmimport --policy-document file://role-policy.json

8. Create a JSON file `container.json` with the following content:

        {
            "Description": "Example image originally in QCOW2 format",
            "Format": "raw",
            "Url": "https://s3-us-west-2.amazonaws.com/raw-images/example.raw"
        }

9. Import the image:

        $ aws ec2 import-snapshot --description "example image" --disk-container file://container.json

10. Finally, if you would like to launch instance with the image, follow [these
AWS
instructions](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html#creating-launching-ami-from-snapshot)
to create an AMI from the snapshot on AWS console.
