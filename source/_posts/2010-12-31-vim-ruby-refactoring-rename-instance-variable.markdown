---
comments: false
date: 2010-12-31 01:14:03
layout: post
slug: vim-ruby-refactoring-rename-instance-variable
title: vim-ruby-refactoring - Rename Instance Variable
wordpress_id: 502
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

**IMPORTANT:** As well as installing the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin, you must also install the [matchit.vim](http://www.vim.org/scripts/script.php?script_id=39) plugin for this refactoring to work.

 

#### Rename Instance Variable

 

Renames the selected instance variable. 

 

#### Example

 

Before refactoring:     
[![RenameInstanceVar_Before](http://justinram.files.wordpress.com/2010/12/renameinstancevar_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/renameinstancevar_before.png)      
Visually select the instance variable you wish to rename      
Hit your **<leader-key>** then type **rriv        
**You will now see a prompt to enter the new variable name:   
Rename to: new_name

 

After refactoring:     
[![RenameInstanceVar_After](http://justinram.files.wordpress.com/2010/12/renameinstancevar_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/renameinstancevar_after.png)      
The instance variable _**@name**_ has been renamed to **_@new_name_** in both locations within the class.

 

**rriv** is the default binding for this refactoring, think **R**efactor **R**ename **I**nstance **V**ariable.
