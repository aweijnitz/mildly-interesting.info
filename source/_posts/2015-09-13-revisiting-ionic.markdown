---
layout: post
title: "Revisiting Ionic"
date: 2015-09-13 08:41:35 +0200
comments: false
published: true
categories: mobileDev
---
When Ionic first came out, I took it for a spin and I was really excited
about what I saw. Now, a couple of years down the line, I decided to
revisit it too see what it has become.
<!-- more -->
[Ionic](http://ionicframework.com/) is basically a frontend (UI) framework that makes it easy to
develop hybrid mobile apps for iOS and Android. It relies on Cordova
and Android SDK for the basics and then adds own services and widges
on top of that. In a way, Ionic is similar to [Trigger.io](https://trigger.io/).

Ionic is based on the [Node.js](https://nodejs.org) eco system of tools and you interact with it
over a CLI based tool called 'ionic'. Anyone familiar with HTML5, Javascript,
AngularJS and Node.js will feel right at home. One advantage of a
command line entry point, is of course that it integrates easily
into your favourite development environment and into automated build
systems as well.

Having everything available through a command line is really nice and
it is generally how I prefer it. It
keeps a clean separation of concerns and you can then compose your own
tool-chain, by simply stiching together the right commands using
scripting. It is also very automation friendly.

## Setting up
The [Getting Started](http://ionicframework.com/getting-started/) page makes a good job of explaining it, but assuming you
alreay have XCode installed (I am on Mac OSX), then it basically boils
down to

```bash Installing Ionic
$ npm install -g cordova ionic ios-sim
```

## Developer experience
If you come from a background of modern web development, the overall
developer experience with Ionic is very familiar and smooth. [Gulp](http://gulpjs.com/) is
used as the base task runner, along with [npm](https://www.npmjs.com/)
and [bower](http://bower.io/) for package management.

Generally, you will develop your app in "web mode" in a browser for quick
tunraround times, and then double check in the emulator now and then
to make sure you are on track.

```bash Developing in "web mode"
$ ionic serve
```

```bash Compiling and running the app in the iOS emulator
$ ionic emulate ios
```

## Scaffolding a new app
Ionic comes with a template system that allows you to quickly create
an app scaffold. It will create a project for you and add in the basic
dependencies.

*Example:* Create a basic app with a native side menu on the left.

```bash
$ ionic start myApp sidemenu
```

The scaffolding command (start) results in this folder structure. It
is pretty much your standard web application project with cordova
plugged in and then some extra settings and config for Ionic.
Familiar, nice and quite clean.

```
.
├── bower.json
├── config.xml
├── gulpfile.js
├── hooks
│   ├── README.md
│   └── after_prepare
├── ionic.project
├── package.json
├── platforms
│   ├── ios
│   └── platforms.json
├── plugins
│   ├── com.ionic.keyboard
│   ├── cordova-plugin-console
│   ├── cordova-plugin-device
│   ├── cordova-plugin-splashscreen
│   ├── cordova-plugin-whitelist
│   ├── fetch.json
│   └── ios.json
├── scss
│   └── ionic.app.scss
└── www
    ├── css
    ├── img
    ├── index.html
    ├── js
    ├── lib
    └── templates

17 directories, 11 files
```


## Previewing apps on devices
There is "View App" app which can be downloaded and installed in
mobile devices. Assuming you have that installed, inviting someone to
checkout your app is as easy as 'ionic share EMAIL'.

## Summing up
First impressions last, and while I still haven't actually tried to
develop a more complex project, which is the real litmus test for any
framework, I have reason to believe Ionic could do well. This is based on
the observation that Ionic observes separation of concerns quite well
and doesn't try to perform a lot of magic for you. It simply stiches
together well-known, tried and tested frameworks like Cordova, Angular
and Sass and adds its own componens to that. It is transparent and
they seem to have made it work.

Now I just need to find a suitable project.
