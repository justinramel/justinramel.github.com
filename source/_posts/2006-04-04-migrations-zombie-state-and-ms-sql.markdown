---
comments: true
date: 2006-04-04 13:28:44
layout: post
slug: migrations-zombie-state-and-ms-sql
title: Migrations 'Zombie State' and MS SQL
wordpress_id: 53
categories:
- Ruby on Rails
---

Getting 'Zombie State' errors with migrations and MS SQL Server? Add the following to your config/enviroment.rb:


    
    
    ActiveRecord::Base.connection.instance_variable_get("@connection")["AutoCommit"] = false
    
