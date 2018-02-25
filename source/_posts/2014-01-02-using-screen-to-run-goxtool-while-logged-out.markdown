---
layout: post
title: "Using Screen to run Goxtool while logged out"
date: 2014-01-02 21:36:58 +0100
comments: true
categories: bitcoin MtGox
---
The Goxtool trading platform supports deployment of automated trading strategies/agents that will trade for you while you are logged in and running the application. However, ideally you would of course rather like to run them _all the time_, so that your brilliant strategies don't miss critical shifts in the price curve. This is extra true for such a volatile currency such as Bitcoin of course.
<!-- more -->
Fortunately running Goxtool in the background is easily achieved. Since Goxtool is a console application, you can use your usual array of *nix tools to manage it. The go-to tool in this case is Screen and I had almost forgotten about it. 

Screen basically lets you detach the current console and put the process in the background while it continues to run, just like if the window/termainal is still active. As with most tools under Linux, you can do a lot with screen, but for this for this purpose, you only need to know three things.

``` bash Basic screen usage
# Start a screen session
$ screen -s mygoxsession 

# Start goxtool as usual in the screen session
$ ./goxtool.py --strategy=buy.py,sell.py

# While the application is running, press 'CTRL-a' followed by 'd' to detach. Then you can logout
CTRL-a d

# At a later point, reattaching to the goxtool session is done like this
$ screen -x mygoxsession 
```
 
Easy as pie! :-)

You can read a little more about screen here.

- [Screen quick ref.](http://aperiodic.net/screen/quick_reference)
- [Screen HOWTO](http://www.debuntu.org/how-to-screen-the-ultimate-admin-tool/)