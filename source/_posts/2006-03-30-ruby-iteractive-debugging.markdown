---
comments: true
date: 2006-03-30 22:06:48
layout: post
slug: ruby-iteractive-debugging
title: Ruby iteractive debugging
wordpress_id: 42
categories:
- Ruby
---

Buggy code, me? Never! If you have a problem with buggy code though your in luck ruby has a debugger baked in:

Simply run ruby with the debug flag:


    
    
    ruby –r debug test.rb
    



**USEFUL COMMANDS**

**list** - List the source code, pass in a number range to filter the list. For example to list the lines 1 to 9:


    
    list 1-9



**b** – Set a break point, pass a line number to break on. For example to break on line 7:


    
    b 7



**c** – Continue program until breakpoint or end of program

**disp** – Display the contents of a variable. For example to see the contents of the look_at_me variable:


    
    display look_at_me



**watch** – Set a watchpoint on a variable. For example to break when the variable meaning_of_life equals 42:


    
    watch meaning_of_life=42
    c



**del** – Delete a breakpoint or watchpoint. For example to delete the first breakpoint we created:


    
    del 1
