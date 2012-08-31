---
comments: false
date: 2006-04-07 20:39:21
layout: post
slug: connecting-ruby-on-rails-to-microsoft-sql-server
title: Connecting Ruby on Rails to Microsoft SQL Server
wordpress_id: 57
categories:
- Ruby on Rails
---

**NOTE: These instructions are now seriously out of date. You may want to check out my always up to date ebook instead. [The secret of connecting Rails to Microsoft SQL Server](http://rails2ms-sql.heroku.com/)**

[![](http://justinram.files.wordpress.com/2010/12/banner.png)](http://rails2ms-sql.heroku.com/)

It appears rails does not connect to MS SQL Server right out of the box.  You need to do the following to get the connection to work:

Get the latest source distribution of [Ruby-DBI](http://rubyforge.org/projects/ruby-dbi/) and copy the file:

    
    bdi-0.1.0/lib/dbd/ADO.rb


to:

    
    c:/ruby/lib/ruby/site_ruby/1.8/DBD/ADO/ADO.rb


**NOTE: The ADO directory does not exist on a standard install, you will need to create it.**

Then simply set up your railsapp/config/database.yml

Here’s an example for reference:

    
    
    development:
      adapter: sqlserver
      database: database_name
      host: server_name
      username: user_name
      password: your_pw_here
    
