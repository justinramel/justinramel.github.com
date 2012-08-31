---
comments: false
date: 2010-12-31 00:27:45
layout: post
slug: vim-ruby-refactoring-extract-local-variable
title: vim-ruby-refactoring - Extract Local Variable
wordpress_id: 485
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Extract Local Variable

 

Extracts a visual selection into a local variable. 

 

The refactoring: [http://www.refactoring.com/catalog/introduceExplainingVariable.html](http://www.refactoring.com/catalog/introduceExplainingVariable.html)

 

#### Example

 

Before refactoring:     
[![ExtractVar_Before](http://justinram.files.wordpress.com/2010/12/extractvar_before_thumb1.png)](http://justinram.files.wordpress.com/2010/12/extractvar_before1.png)      
Visually select the value you wish to extract      
Hit your **<leader-key>** then type **relv        
**You will now see a prompt to enter the variable name:   
Variable name: mac_os

 

After refactoring:     
[![ExtractVar_After](http://justinram.files.wordpress.com/2010/12/extractvar_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractvar_after.png)      
The value **_platform.upcase.include?(‘MAC’)_** has been extracted into a local variable **_mac_os_**.

 

**relv** is the default binding for this refactoring, think **R**efactor **E**xtract **L**ocal **V**ariable.
