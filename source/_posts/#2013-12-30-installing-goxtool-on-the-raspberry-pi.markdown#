---
layout: post
title: "Installing GoxTool on the Raspberry Pi"
date: 2013-12-30 20:27:28 +0100
comments: true
categories: Bitcoin RaspberryPi
---
[GoxTool](https://github.com/caktux/goxtool) is a Bitcoin trading tool written in Python which allows automated trading on the [MtGox bitcoin exchange](https://www.mtgox.com/) using a terminal application. It is the software plaform that powers [ZeroGox](https://zerogox.com/), but you can set it up for yourself as well and this is what I tried to do.

In theory, the installation is straight forward; You clone the repo from GitHub and then start the application, provided you have Python installed. If you are running a Raspberry Pi however, it turned out to require a couple of extra steps to get it going. 

## This is what you need to do to prepare for the actual installation
First you will need to install the Python package manager _pip_ and then the Python development extensions (_Python.h_ specifically), which in turn will get you to the end goal of being able to use pip to install the _pycrypto_ library which is needed in order to run goxtool.

All-in-all, this is what you need to do

``` bash Installing pip
$ sudo apt-get install python-pip
$ sudo apt-get install python-dev
$ sudo pip install pycrypto
```

__When things don't work out you will see stuff like this__

``` bash Typical errors for missing components
# You are missing the pycryto library
[…] ImportError: No module named Crypto.Cipher 

# You are trying to compile the pycryto library, but you are missing the Python development extensions
[…] src/MD2.c:31:20: fatal error: Python.h: No such file or directory

``` 

## Installing and running goxtool
Once you have everyhing in place, following the instructions at the [GoxTool GitHub page](https://github.com/caktux/goxtool) is straight forward. Make sure you read them, but essentially it boils down to cloning the repository and then running the tool.
``` bash
git clone git://github.com/caktux/goxtool.git
cd goxtool
./goxtool.py
```

You should be seeing something like this once everything is working and the application is running.

{% img  /images/posts/goxtool.png Goxtool running on a Rasberry Pi %}

 
_Good luck!_





