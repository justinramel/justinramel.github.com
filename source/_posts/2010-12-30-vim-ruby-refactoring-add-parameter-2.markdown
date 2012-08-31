---
comments: false
date: 2010-12-30 17:10:35
layout: post
slug: vim-ruby-refactoring-add-parameter-2
title: vim-ruby-refactoring - Add Parameter
wordpress_id: 429
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Add Parameter

 

Simply adds a parameter (or many separated with commas) to a method.

 

The refactoring: [http://www.refactoring.com/catalog/addParameter.html](http://www.refactoring.com/catalog/addParameter.html)

 

#### Example

 

Before refactoring:[![AddParameter_Before](http://justinram.files.wordpress.com/2010/12/addparameter_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/addparameter_before.png)       
Move your cursor onto the method where you wish to add the parameter       
Hit your **<leader-key>** then type **rap        
**You will now see a prompt to enter the parameter name:       
Parameter name: **date**

 

After refactoring:

 

[![AddParameter_After](http://justinram.files.wordpress.com/2010/12/addparameter_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/addparameter_after.png)       
The contact method now has a date parameter added.

 

**rap** is the default binding for this refactoring, think **R**efactor **A**dd **P**arameter.

 

The default **<leader-key>** in vim is the ‘\’ key but you can remap this to any key you like.
