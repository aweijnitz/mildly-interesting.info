---
layout: post
title: "Installing Wildfly 8 for development"
date: 2014-02-12 22:23:18 +0100
comments: true
categories: jee, java, wildfly
---
Yesterday, [Wildfly 8](http://www.wildfly.org/) was released in the final version (8.0.0.Final) and I thought I'd share how I set it up for development. As you will see, there is nothing much to it which I see as a very good sign.

So, make sure you have a modern Java version installed, and then do this:


## Download and unpack it
``` bash Download and install
$ curl -O http://download.jboss.org/wildfly/8.0.0.Final/wildfly-8.0.0.Final.tar.gz
$ tar xzf wildfly-8.0.0.Final.tar.gz
$ cd wildfly-8.0.0.Final/bin
```

## Make sure it can start
``` bash Start Wildfly and open browser
$ ./standalone.sh
$ open http://localhost:8080
```
At this point, you should see the Wildfly welcome screen. 

![Wildfly8 welcome screen](https://docs.jboss.org/author/download/attachments/66322959/wildfly.png?version=1&modificationDate=1392178048000)


## Make it insecure

Security is good, but it does get in your way when developing. In order to work with the server you need to add an administrator user. Doing so is very easy, but the default password policy settings make life as a developer  uneccessary hard (reasonable security is enforced).

In order to make life more convenient for local development, you can however disable all of the annoying security policies by editing the file add-user.properties.

``` bash Make it insecure and add admin user

# Assuming you are in [...]wildfly-8.0.0.Final/bin
$ emacs add-user.properties

# In emacs, switch off all security settings. 
password.restriction.minLength=2
password.restriction.minAlpha=0
password.restriction.minDigit=0
password.restriction.minSymbol=0
password.restriction.mustNotMatchUsername=FALSE
# Disable list of forbidden passwords
#password.restriction.forbiddenValue=root,admin,administrator
password.restriction.strength=VERY_WEAK

```

## Add user admin/admin
Now you are ready to add your standard development administrator user: admin, password: admin. :-)

``` bash Add admin user
$ ./add-user.sh (follow on-screen instrucitons)

```
The full installation and getting started guide can be found here. It is quite good actually. [WildFly8 Getting Started](https://docs.jboss.org/author/display/WFLY8/Getting+Started+Guide)


_Enjoy!_




