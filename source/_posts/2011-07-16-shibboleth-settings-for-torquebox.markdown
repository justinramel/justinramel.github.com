---
comments: false
date: 2011-07-16 22:14:52
layout: post
slug: shibboleth-settings-for-torquebox
title: Shibboleth settings for TorqueBox
wordpress_id: 562
categories:
- torquebox
---

#### Authentication Settings


Notes on setting up Shibboleth against an Apache Reverse Proxy to TorqueBox.

Config File: /etc/httpd/conf.d/shib.conf

`  ShibUseHeaders On
  AuthType shibboleth
  ShibRequestSetting requireSession 1
  require valid-user
`

The '`ShibUseHeaders On`' setting tells Shibboleth to pass along its attributes as request headers so your sinatra/rails application can gain access to them allowing you to implement your own authorisation system.



#### Simple Authorisation


If you don't need a complex authorisation system and you don't mind users seeing a standard Shibboleth authorisation error page:

[![](http://justinram.files.wordpress.com/2011/07/shib1.png?w=300)](http://justinram.files.wordpress.com/2011/07/shib1.png)

You can implement this via your Shibboleth settings using the require statement:

`  ShibUseHeaders On
  AuthType shibboleth
  ShibRequestSetting requireSession 1
  **require grouper_groups ~ MySecurityGroup**
`

Here we require the custom grouper_groups attribute matches on the regular expression after the '`~`'. Basically to access the protected url the user must be a member of the MySecurityGroup.



##### Top Tip


When playing with your Shib settings don't forget to restart httpd to see the affect.
`sudo /sbin/service httpd restart`
