---
comments: false
date: 2010-12-30 21:37:59
layout: post
slug: vim-ruby-refactoring-inline-temp
title: vim-ruby-refactoring - Inline Temp
wordpress_id: 446
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

#### Inline Temp

 

Replaces a temporary variable with a direct call to the method or formula.

 

The refactoring: [http://www.refactoring.com/catalog/inlineTemp.html](http://www.refactoring.com/catalog/inlineTemp.html)

 

#### Example

 

Before refactoring:

 

[![InlineTemp_Before](http://justinram.files.wordpress.com/2010/12/inlinetemp_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/inlinetemp_before.png)       
Move the cursor onto the temp variable (in this case base_price)       
Hit your **<leader-key>** then type **rit        
**

 

After refactoring:

 

[![InlineTemp_After](http://justinram.files.wordpress.com/2010/12/inlinetemp_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/inlinetemp_after.png)       
The temp variable base_price has been replace with a direct call to the method and we’ve saved a line of code.

 

**rit** is the default binding for this refactoring, think **R**efactor **I**nline **T**emp.
