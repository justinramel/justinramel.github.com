---
comments: true
date: 2006-05-08 10:41:58
layout: post
slug: sap-netwweaver-developer-studio-compile-error
title: SAP NetWeaver developer Studio – Compile Error
wordpress_id: 80
categories:
- SAP Enterprise Portal
---

Was getting weird error when trying to compile a project today:

`The project was not built due to "Problems encountered while copying resources.". Fix the problem, then try refreshing this project and rebuilding it since it may be inconsistent.`

After a quick Google it appears this has happened to others and a re-install fixed the problem.  I managed to fix the problem by:

Highlighting the project in the Enterprise Portal perspective then doing a File => Refresh from the menu.
