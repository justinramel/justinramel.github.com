---
comments: false
date: 2011-07-16 21:16:31
layout: post
slug: setup-apache-reverse-proxy-to-torquebox
title: 'Setup Apache Reverse Proxy to Torquebox '
wordpress_id: 557
categories:
- General
- torquebox
---

Setup Apache as a Reverse Proxy in front of a standalone Torquebox server.



#### Apache Setup





##### Proxy Module



For this to work Apache must have the mod_proxy module loaded:

[http://httpd.apache.org/docs/2.1/mod/mod_proxy.html](http://httpd.apache.org/docs/2.1/mod/mod_proxy.html)

Config file: /etc/httpd/conf/httpd.conf

`ProxyRequests     Off 						   # Switch off forward proxy
ProxyPreserveHost On 							   # Pass host name onto the proxy
ProxyPass         /myapp http://localhost:8080/myapp/  # Map url to remote server 
ProxyPassReverse  /myapp http://localhost:8080/myapp/  # Adjust header sent from remote server to match url
`
Here we are passing all calls to the /myapp/ url on to the Torquebox server http://localhost:8080/myapp/



#### TorqueBox Setup



In your Torquebox application folder create a file 'config/torquebox.yml' which contains a context which matches the Apache reverse proxy url.

torquebox.yml

web:
  context: /myapp
ruby:
  version: 1.9
