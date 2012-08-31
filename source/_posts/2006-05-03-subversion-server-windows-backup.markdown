---
comments: true
date: 2006-05-03 10:46:34
layout: post
slug: subversion-server-windows-backup
title: Subversion server + windows + backup
wordpress_id: 75
categories:
- General
---

So you want to backup your repository?

Unfortunately you cannot do a straight backup of your repository as someone may have a file open/locked which will cause problems on restore. So you should do a "hot copy" to prevent any locking issues when the actual backup is made.  My "hot copy" is created using the following batch file:

    
    
    REM Reset hot copy
    rmdir /S /Q c:\\svnrepos_hotcopy
    mkdir c:\\svnrepos_hotcopy
    
    REM Initiate SVN backup. Use svadmin hotcopy --help for details
    svnadmin hotcopy c:\\svnrepos c:\\svnrepos_hotcopy --clean-logs
    


I run this batch file daily as a scheduled task before the actual backup.

This batch file is a modification of the batch file described over at:

[Blended Technologies](http://www.blendedtechnologies.com/daily-backup-of-subversion/21)
