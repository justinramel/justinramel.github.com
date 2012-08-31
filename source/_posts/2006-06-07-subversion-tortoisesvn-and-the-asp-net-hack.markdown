---
comments: true
date: 2006-06-07 11:15:08
layout: post
slug: subversion-tortoisesvn-and-the-asp-net-hack
title: Subversion, TortoiseSVN and the _SVN ASP.NET Hack
wordpress_id: 97
categories:
- Subversion
---

Good write up of the TortoiseSVN ASP.NET Hack [here](http://www.codefez.com/Home/tabid/36/ctl/ArticleView/mid/364/articleId/191/Subversion-and-the-ASP-NET-Hack.aspx)

Basically involves creating an environment variable SVN_ASP_DOT_NET_HACK with the value of 1. When TortoiseSVN finds this variable it looks for _svn folder instead of .svn
