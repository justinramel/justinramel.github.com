---
comments: true
date: 2006-12-05 12:25:36
layout: post
slug: sap-portal-how-do-i-reference-a-javascript-file
title: SAP Portal how do I reference a Javascript file?
wordpress_id: 34
categories:
- SAP Enterprise Portal
---

Easy when you know how


    
    request = (IPortalComponentRequest)this.getRequest();
    response = (IPortalComponentResponse)this.getResponse();
    IResource jsResource = request.getResource(IResource.SCRIPT, “scripts/myscript.js”);
    response.addResource(jsResource);
