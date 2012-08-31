---
comments: false
date: 2011-07-20 19:19:55
layout: post
slug: upload-files-to-sharepoint-from-linux
title: Upload files to Sharepoint from linux
wordpress_id: 572
categories:
- General
---

#### Fortress




It seemed almost impossible to penetrate the fortress that is Sharepoint with only NTLM authentication enabled. Turns out its really easy when you know how.





#### curl to the rescue!




You can upload files using curl directly into Sharepoint via it's HTTP PUT interface.



`curl --ntlm --user username:password --upload-file myfile.xls https://sharepointserver.com/sites/mysite/myfile.xls`



Told you, easy when you know how.
