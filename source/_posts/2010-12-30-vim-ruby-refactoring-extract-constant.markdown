---
comments: false
date: 2010-12-30 23:04:56
layout: post
slug: vim-ruby-refactoring-extract-constant
title: vim-ruby-refactoring - Extract Constant
wordpress_id: 465
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Extract Constant

 

Extracts a selection into a constant which is placed at the top of the current module or class.

 

The refactoring: [http://www.refactoring.com/catalog/replaceMagicNumberWithSymbolicConstant.html](http://www.refactoring.com/catalog/replaceMagicNumberWithSymbolicConstant.html)

 

#### Example

 

Before refactoring:     
[![ExtractConstant_Before](http://justinram.files.wordpress.com/2010/12/extractconstant_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractconstant_before.png)   
Visually select the value you wish to extract      
Hit your **<leader-key>** then type **rec        
**You will now see a prompt to enter the constant name:   
Constant name: Gravitational_Constant

 

After refactoring:     
[![ExtractConstant_After](http://justinram.files.wordpress.com/2010/12/extractconstant_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/extractconstant_after.png)      
The value **_9.81_** has been extracted into a constant **_GRAVITATIONAL_CONSTANT_** which is placed at the top of the module.

 

**rec** is the default binding for this refactoring, think **R**efactor **E**xtract **C**onstant.
