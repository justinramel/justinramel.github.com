---
comments: false
date: 2010-12-30 22:37:07
layout: post
slug: vim-ruby-refactoring-convert-post-conditional
title: vim-ruby-refactoring - Convert Post Conditional
wordpress_id: 457
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Convert Post Conditional 

 

Converts a post conditional expression to a conditional expression.

 

#### Example

 

Before refactoring:

 

[![ConvertPostConditional_Before](http://justinram.files.wordpress.com/2010/12/convertpostconditional_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/convertpostconditional_before.png)       
Move the cursor onto the line which contains the post conditional expression       
Hit your **<leader-key>** then type **rcpc        
**

 

After refactoring:

 

[![ConvertPostConditional_After](http://justinram.files.wordpress.com/2010/12/convertpostconditional_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/convertpostconditional_after.png)       
The post conditional expression is split across 3 lines and converted into a standard if expression.

 

**rcpc** is the default binding for this refactoring, think **R**efactor **C**onvert **P**ost **C**onditional.
