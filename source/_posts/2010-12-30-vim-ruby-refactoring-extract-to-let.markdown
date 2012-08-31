---
comments: false
date: 2010-12-30 23:49:00
layout: post
slug: vim-ruby-refactoring-extract-to-let
title: vim-ruby-refactoring - Extract to Let
wordpress_id: 472
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Extract to Let

 

This is an [RSpec](http://rspec.info/) specific refactoring which will extract an initialisation line and create a let method for you.

 

#### Example

 

Before refactoring:     
[![ExtractLet_Before](http://justinram.files.wordpress.com/2010/12/extractlet_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractlet_before.png)   
Move the cursor on to the line you wish to extract      
Hit your **<leader-key>** then type **rel **

 

After refactoring:     
[![ExtractLet_After](http://justinram.files.wordpress.com/2010/12/extractlet_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractlet_after.png)      
The let method is created above the it block, using the initialisation line - account = Account.new.

 

**rel** is the default binding for this refactoring, think **R**efactor **E**xtract **L**et.
