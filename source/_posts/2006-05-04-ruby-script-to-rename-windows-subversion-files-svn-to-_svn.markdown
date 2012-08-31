---
comments: true
date: 2006-05-04 21:46:34
layout: post
slug: ruby-script-to-rename-windows-subversion-files-svn-to-_svn
title: Ruby script to rename windows subversion files .svn to _svn
wordpress_id: 77
categories:
- Ruby
- Subversion
---


    Dir["**/.svn"].each do |folder|
    	File.rename(folder, folder.sub('.svn', '_svn'))
    end
    
