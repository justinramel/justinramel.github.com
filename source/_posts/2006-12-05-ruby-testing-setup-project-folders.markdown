---
comments: true
date: 2006-12-05 12:24:58
layout: post
slug: ruby-testing-setup-project-folders
title: Ruby testing - setup project folders
wordpress_id: 40
categories:
- Ruby
- Testing
---

Its a good idea to keep your test cases seperate from your production code:


    
    
      myproject
          lib/
              workomatic.rb
          test/
              test_workomatic.rb
    



When you have your project setup in this way add the following line to the top of your test cases:

Inside test_workomatic.rb

    
    
      $:.unshift File.join(File.dirname(__FILE__), "..", "lib")
      require workomatic.rb
    
