---
layout: post
title: "Packer.io for the impatient"
date: 2015-01-26 23:43:48 +0100
comments: false
categories: 
---
Packer is a great tool, but unfortunately it has a couple of minor
issues in the getting started guide which snags you. This is a quick
write-up to get yourself through those first hurdles quickly.

<!-- more -->

__Setting up an Amazon EC2 Debian image with Oracle Java 8__

__Problems I encountered__

- Using the shell provisioner, you cannot source sub scripts easily
- The usual Oracle Java 8 non-interactive shell script example doesn't work
- The AMI image in the getting started guide on packer.io doesn't exist anymore


I won't go into detail on what I tried and not, but instead I will just focus
on the [final working scripts](https://github.com/aweijnitz/packerio_amazon_image).

If you are really impatient, you can skip everything below and just
checkout the file from the link above, plug in your credentials in the
build script and take it from there.

If you have some more time before you dig into the below, head over and read through the
[Getting Started Guide](https://packer.io/intro/getting-started/setup.html)
at packer.io.

## Configuring a basic working image
The first hurdle was that the copy-paste example from packer.io didn't
work. It turned out that the image they used as a starting point
doesn't exist anymore and you will have to plug in your own image ID.

[This page](https://wiki.debian.org/Cloud/AmazonEC2Image/Wheezy) lists
Debian Amazon images.

Pick an image id which matches your region. Pick it from the column *"hvm x86_64 ebs"* to be able to run it on the free
tier in Amazon EC2. Edit builders section in the JSON file to reflect the image id.

Example

```
    "region": "eu-west-1",
    "source_ami": "ami-a345c3d4",
```

## Understanding the Java 8 workaround
For me, getting the non-interactive Oracle Java 8 installation simply
didn't work at all. In the end, I had to make a script that downloads
the actual installation script and runs the downloaded script as root
using sudo.

It is a weird workaround and there is probably a better way, but this
one works just as well, so I won't bother any more at this point.

This is my
[installer downloader](https://github.com/aweijnitz/packerio_amazon_image/blob/master/provisioning/scripts/installJava8.sh).
It downloads and runs this [Java 8 installation script](https://gist.github.com/aweijnitz/92bbb761c9e407809193). 

## Packing it
It couldn't be simpler, just tell packer about your amazon details and
point it to the description file. *Hint:* Set the details as environment
variables in your shell login script to avoid accidental sharing.

```bash
packer build -var 'aws_access_key=YOUR AMAZON ACCESS KEY' -var \
'aws_secret_key=YOUR AMAZON SECRET KEY' basic_java8_image.json
```

The line is quite long, so I bundled it up in a shell script and
called it ```build.sh``` in the repo.

## Launching the image
Once packer is done, just head over to the Amazon Management Console
and you will find the freshly created image under Images > AMIs.
That is also where you launch it from.

Good luck!
















