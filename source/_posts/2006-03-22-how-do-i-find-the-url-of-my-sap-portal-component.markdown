---
comments: true
date: 2006-03-22 14:49:29
layout: post
slug: how-do-i-find-the-url-of-my-sap-portal-component
title: How do I find the url of my SAP Portal Component?
wordpress_id: 29
categories:
- SAP Enterprise Portal
---

Try this…

In SAP Netweaver Developer Studio

Open your project

Open the file:


    
    MyPortalProject
        dist
            PORTAL-INF
                Portalapp.xml



You should now see a “Run…” button for each portal component in your project

Click the “Run…” button and the dev studio will open up a new browser window with the url to your component.
