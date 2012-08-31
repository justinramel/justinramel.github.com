---
comments: true
date: 2006-03-20 12:30:50
layout: post
slug: installing-subclipse-for-sap-netweaver-developer-studio-2013
title: Installing Subclipse for SAP NetWeaver Developer Studio 2.0.13
wordpress_id: 25
categories:
- SAP Enterprise Portal
---

First download the correct version of Subclipse:

[Download the Eclipse 2.x version](http://subclipse.tigris.org/files/documents/906/22688/org.tigris.subversion.subclipse_0.9.3.3.zip)

Extract the zip file and copy the two folders:


    
    org.tigris.subversion.subclipse.core_0.9.3.3
    org.tigris.subversion.subclipse.ui_0.9.3.3



To your plugins folder, in my case:


    
    C:\\Program Files\\SAP\\JDT\\eclipse\\plugins



Fire up the developer studio and you should now have the subversion perspective available.

Menu: Window => Open Perspective => Other…

Select SVN Repository Exploring from the dialog.

Right click on the SVN Repository windows to add a new repository:

Menu: New => Repository Location…

You will now see the following dialog:

![New Repository Dialog](http://justinram.files.wordpress.com/2006/03/repository.jpg)

Simply enter your subversion server address and user/password if required.

You should now see your source code, right click on the Trunk folder of a project and select Check Out as Project.

Cogs will start turning and when finished you will have a shiny new project to play with.
