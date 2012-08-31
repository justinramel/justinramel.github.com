---
comments: true
date: 2006-02-27 10:57:00
layout: post
slug: installing-watir-via-the-gem-utility
title: Installing Watir via the gem utility
wordpress_id: 12
categories:
- Watir
---

The install should be as simple as dropping into dos, cd to your Ruby folder and run the command:
`gem install watir`

Unfortunately it wasn’t that simple for me, we work via a proxy here so I had to tell the gem utility about it.

**Running gem install when you are behind a proxy**

Set the HTTP_PROXY environment variable.

Example:
`set HTTP_PROXY=http://mycache:8080`

You can now run:
`gem install watir`

Or you can pass the proxy information as a parameter to gem via the -p switch:

`gem install watir -p http://mycache:8080`

Gem will now go off download and install the latest Watir package, version 1.4.1 in my case.  Be patient this can take some time depending on server load.
