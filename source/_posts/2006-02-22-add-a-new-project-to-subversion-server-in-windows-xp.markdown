---
comments: true
date: 2006-02-22 12:12:00
layout: post
slug: add-a-new-project-to-subversion-server-in-windows-xp
title: Add a new project to Subversion server in Windows XP
wordpress_id: 7
categories:
- Programming
---

NOTE: You must have [TortoiseSVN](http://tortoisesvn.tigris.org/) installed for these instructions to work!

First create your Project folder structure:

    
    ProjectName
    branches
    tags
    trunk


Place your source in the trunk folder.

In windows explorer right click on ProjectName folder and select TortiseSVN -> Import from the menu.

You will now see the import screen:

[![](http://photos1.blogger.com/blogger/752/2322/320/svnimport.jpg)](http://photos1.blogger.com/blogger/752/2322/1600/svnimport.jpg)
Enter the repository/ProjectName an import message and click OK.

You have now created the project in Subversion but you must still check out the source you just imported.  This can be done via TortoiseSVN or directly in eclipse using the [subclipse](http://subclipse.tigris.org/) add in.
