---
layout: post
title: "Get started with Yeoman, Grunt and the AngularJS generator"
date: 2014-04-24 21:06:48 +0200
comments: false
categories: javascript workflow angularjs grunt yeoman CI
---
I have been hesitant to move into "managed workflows" for my
Javascript development. Mostly this is because nine times out of ten, the projects I do in my spare time are super basic and I feel I rather keep it clean and transparent, than adding in a lot of cruft. That said, I finally decided to give Yeoman and Grunt a go.
<!-- more -->
Workflow frameworks and helpers like [Grunt](http://gruntjs.com/), [Gulp](http://gulpjs.com/), [Yeoman](http://yeoman.io/), [Bower](http://bower.io/), [Compass](http://compass-style.org/) and what not are great, but mostly overkill for simple things. It's like when you start generating classes in an enterprise class IDE and end up with thousands of lines of code that you don't know if you need or not. If you are unsure about the underlying technologies, you will be lost at the first unexpected exception in the generated code.

This is not to say I dislike IDEs, quite opposite, I use [WebStorm](http://www.jetbrains.com/webstorm/) a lot, but as with any tool, you need to pick the right one for the task at hand. I use [Sublime Text](http://www.sublimetext.com/) daily and I am currently writing this text in good old [Emacs](http://www.gnu.org/software/emacs/).

Anyway, lately I decided that Yeoman probably can help me after all, or at least I should know more about it, so I decided to take it for a spin. Since I like AngularJS as well, I decided to install the Yeoman official AngularJS generator in the same go. The experience made me write this post, so that if I have to do it again, I have a place to find all the commands needed. :-)

This is a quick summary of all the commands needed to get up and going with yeoman and the angularJS generator on MacOSX. I have it working in Windows as well and the commands are the same.

For my memory and for anyone that also needs them.

``` bash Getting yeoman with the angularJS generator installed
# Assuming you have Ruby and Node.js previously installed
sudo gem install compass
npm install -g yo
npm install -g generator-angular

# Ok, the global commands are now in place.
# Time to make our first project.

mkdir my-new-project && cd $_ 
yo angular MyAngularApp
npm install
bower install
npm install grunt-karma --save-dev
npm install karma-jasmine --save-dev
npm install --save-dev karma-chrome-launcher
grunt

# Everything should be ok, so start developing
grunt serve
```

Good Luck!



