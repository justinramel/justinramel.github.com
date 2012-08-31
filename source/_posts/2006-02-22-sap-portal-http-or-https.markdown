---
comments: true
date: 2006-02-22 11:36:00
layout: post
slug: sap-portal-http-or-https
title: SAP Portal HTTP or HTTPS?
wordpress_id: 6
categories:
- SAP Enterprise Portal
---

Want to tell if your iView is running over HTTP or HTTPS?

Try this:

WARNING: Untested code ahead!
`
HttpServletRequest servletRequest = componentRequest.getServletRequest();
String requestURL = servletRequest.getRequestURL().toString();
String protocol = requestURL.substring(0, requestURL.indexOf(":"));`

if(protocol.equals("http"))
{
// do HTTP stuff
}
else
{
// do HTTPS stuff
}
