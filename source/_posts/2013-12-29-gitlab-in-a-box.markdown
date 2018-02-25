---
layout: post
title: "GitLab in a box"
date: 2013-12-29 19:08:37 +0100
comments: true
categories: DevOps VirtualBox Vagrant
---
## Putting a production ready GitLab in a Vagrant box
I have been thinking about ways we could gradually switch from Subversion to using Git at work and since I had some time over during the Holidays, I decided to give [Vagrant](http://www.vagrantup.com/) a go.The goal is to quickly be able to setup new project environments using [GitLab](http://gitlab.org/) as the main collaboration and Git managenent system.
<!-- more -->
## Current status
Following the [instructions for prodution installs](https://github.com/gitlabhq/gitlabhq/blob/master/doc/install/installation.md) I managed to setup a production ready, Debian-based GitLab installation in VirtualBox and then bake a Vagrant box out of that. This means a project only has to add users, import their code and optionally change a few passwords to get going with a complete system.

### Downloads
These are the downloads. Read below for instructions.

- [Production installed box](http://mildly-interesting.info/vagrant/gitlab62svn.box)
- [Vagrant file](http://mildly-interesting.info/vagrant/Vagrantfile)

## The end goal
The goal would be to allow quick and easy deployment of a production ready git server for projects to use on-premise, including a way to sync the code back to a central Subversion instance (necessary for our needs). Ideally it should also include a user friendly frontend to ease the switch from Subversion to Git and provide some basic means of collaboration. 

The current box is a good start, but it needs some field testing and a template/docs for projects to easily provision it and hook up Subversion at the back of Git.

## Why?
This is a larger discussion, but in my opinion, git has better support for parallel workflows and it's distributed nature and lightweight branches makes teamwork easier. A local git server is also faster and more flexible to work with than a central Subversion server shared by all projects.

There are one-click installers for GitLab already, but unless I missed something they are either for development only, or for cloud deployment. This one is for on-premise purposes on a local LAN.

## Try it out
The Vagrant box doesn't have any work related software or information on it, so I have made it publically available for download. This is how you get started:

* Install VirtualBox [VirtualBox](https://www.virtualbox.org)
* Install Vagrant [Vagrant](http://www.vagrantup.com/)

In a console/cmd window, assuming VirtualBox and Vagrant are installed already
``` bash Downloading and starting the GitLab Vagrant box
$ mkdir gitlab      # can be any name
$ cd gitlab
$ vagrant init gitlab http://mildly-interesting.info/vagrant/gitlab62svn.box
$ curl http://mildly-interesting.info/vagrant/Vagrantfile > Vagrantfile   
# If you are on Windows, you will have to manually download the Vagrant file using a browser.
# Do any optional provisioning and config of the Vagrantfile here, then
$ vagrant up
# Wait for first download and start
# Profit!
```

Once the box has started, point a browser to localhost and start using the system: [http://localhost:8080](http://localhost:8080) 
_(see login info below)_

### Logins
Each project should change the key passwords, so I made them easy to remember and stuck to some defaults as recommended by Vagrant.

* GitLab admin login: admin@local.host, _password:_ abc123 
* Vagrant user: vagrant, _password:_ vagrant
* Debian default user: debian, _password:_ reverse
* Debian root _password:_ toor
* MySQL root _password:_ abc123 

## What's in the box?
It's basically a clean Debian squeeze dist from the ISO (I used the one fund [here](http://virtualboxes.org/images/debian/) as my starting point), with GitLab, Redis, Ngnix and dependencies added.

You can login to the box using this command (I think you need to be in the folder of the Vagrantfile)
``` bash SSH login
vagrant ssh
```

You can check the status of the box as well
``` bash Box status
vagrant status
```

### Making new boxes from existing ones
If you install additional software, or tweak the box somehow, you can make a new base box to start other projects from. It is really easy, just use the command below with your instance running. The result will be a new box file which you can put on a webserver and use, just like I did with this one.
``` bash Package new box from existing instance (running)
vagrant package
```

Also, if you run into trouble, it is helpful to first start the VirtualBox application and then do _vagrant up_


## Vagrant and GitLab
[Vagrant](http://www.vagrantup.com/) is intended as a development tool to be able to quickly switch between projects and minimizing the time it takes to get new team members up and running. It works like a shell over different virtualization providers and adds local provisioning and some other funtionalities to make it easy to do project specific configurations to a shared base environment. VirtualBox is used as the default virtualization provider in Vagrant and since we are already using VirtualBox in our projects, it is a good basic fit.

[GitLab](http://gitlab.org/) is a browser based UI on top of Git, which provides tools for team collaboration, like managing git repos, access control and collaborating around code. Just as it is necessary to easily get developers up and running using a consistent environment, it is important to quickly be able to establish the supporting systems for a new project, like version control, issue management and continous builds. This is where GitLab comes in. 

There are alternatives to GitLab, like [Gitorious](https://gitorious.org/) and private hosting on Github, but following some googling, I decided to give GitLab a go. I am sure Gitorious is fine as well and GitHub is probably the best, but that comes at a price of course.

And that's about it. Looking forward to hopefully trying it out in real life.
