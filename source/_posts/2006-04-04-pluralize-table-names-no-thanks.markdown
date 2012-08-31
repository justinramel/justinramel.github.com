---
comments: true
date: 2006-04-04 13:05:19
layout: post
slug: pluralize-table-names-no-thanks
title: Pluralize table names - no thanks!
wordpress_id: 52
categories:
- Ruby on Rails
---

Sorry I just can't live with plural table names, I just can't get my head around it! Luckily it is easily turned off. In RadRails there is a simple tick box when creating the project which simply adds the following line to the end of your applications config/environment.rb file:


    
    
    # Include your application configuration below
    ActiveRecord::Base.pluralize_table_names = false
    



I may live to regret not embracing plural table names but I doubt it!
