---
comments: false
date: 2010-12-31 00:59:58
layout: post
slug: vim-ruby-refactoring-rename-local-variable
title: vim-ruby-refactoring - Rename Local Variable
wordpress_id: 496
categories:
- Ruby
- vim
tags:
- ruby vim refactoring vim-ruby-refactoring
---

This post is part of a [series](http://justinram.wordpress.com/2010/12/30/vim-ruby-refactoring-series/) which documents the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin.

 

**IMPORTANT:** As well as installing the [vim-ruby-refactoring](https://github.com/ecomba/vim-ruby-refactoring) plugin, you must also install the [matchit.vim](http://www.vim.org/scripts/script.php?script_id=39) plugin for this refactoring to work.

 

#### Rename Local Variable

 

Renames the selected local variable. 

 

#### Example

 

Before refactoring:     
[![RenameVar_Before](http://justinram.files.wordpress.com/2010/12/renamevar_before_thumb.png)](http://justinram.files.wordpress.com/2010/12/renamevar_before.png)      
Visually select the local variable you wish to rename      
Hit your **<leader-key>** then type **rrlv        
**You will now see a prompt to enter the new variable name:   
Rename to: is_mac_os

 

After refactoring:     
[![RenameVar_After](http://justinram.files.wordpress.com/2010/12/renamevar_after_thumb.png)](http://justinram.files.wordpress.com/2010/12/renamevar_after.png)      
The local variable _**mac_os**_ has been renamed to **_is_mac_os_** in both locations within the method.

 

**rrlv** is the default binding for this refactoring, think **R**efactor **R**ename **L**ocal **V**ariable.
