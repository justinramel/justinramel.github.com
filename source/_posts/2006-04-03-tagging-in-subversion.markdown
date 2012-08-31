---
comments: true
date: 2006-04-03 09:25:29
layout: post
slug: tagging-in-subversion
title: Tagging in subversion
wordpress_id: 47
categories:
- Subversion
---

We have started tagging our source when releasing to QA/porduction which means we can easily roll back to an ealier verison of the code if a problem is found in production. Here's how we do it using TortoiseSVN.

First commit your source then open up the TortoiseSVN repository browser:

Right click in a folder in windows to get a context menu then select TortoiseSVN => Repo-Browser.

You should now see Repository browser:

![Repository Browser](http://justinram.files.wordpress.com/2006/04/repos.thumbnail.JPG)

Find the trunk of the project you wish to tag then right click on the trunk folder and select 'Copy to...' from the context menu.

You will now see the Copy to... dialog:

![CopyTo](http://justinram.files.wordpress.com/2006/04/copyto.thumbnail.JPG)

Enter the path to your tagged copy, along the lines of svn://server/project/tags/Version2.00

You now have tagged version of your project which you can revert to anytime.
