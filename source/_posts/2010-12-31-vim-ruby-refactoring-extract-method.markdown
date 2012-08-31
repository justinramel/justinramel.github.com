---
comments: false
date: 2010-12-31 01:32:57
layout: post
slug: vim-ruby-refactoring-extract-method
title: vim-ruby-refactoring - Extract Method
wordpress_id: 507
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

**IMPORTANT:** As well as installing the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin, you must also install the [matchit.vim](http://www.vim.org/scripts/script.php?script_id=39) plugin for this refactoring to work.

 

#### Extract Method

 

Extracts a selection into a method and places it above the current method.

 

The refactoring: [http://www.refactoring.com/catalog/extractMethod.html](http://www.refactoring.com/catalog/extractMethod.html)

 

#### Example

 

Before refactoring:     
[![ExtractMethod_Before](http://justinram.files.wordpress.com/2010/12/extractmethod_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractmethod_before.png)      
Visually select lines you wish to extract      
Hit your **<leader-key>** then type **rem       
**You will now see a prompt to enter the new method name:   
Method name: print_details

 

After refactoring:     
[![ExtractMethod_After](http://justinram.files.wordpress.com/2010/12/extractmethod_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractmethod_after.png)      
A new method **_print_details_** has been added above the **print_owing** method containing the contents of the selected lines.

 

**rem** is the default binding for this refactoring, think **R**efactor **E**xtract **M**ethod.
