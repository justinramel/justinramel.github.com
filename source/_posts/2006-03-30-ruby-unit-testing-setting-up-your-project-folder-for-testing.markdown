---
comments: true
date: 2006-03-30 21:22:01
layout: post
slug: ruby-unit-testing-setting-up-your-project-folder-for-testing
title: Ruby unit testing - Setting up your project folder for testing
wordpress_id: 41
categories:
- General
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
    



Now when you run this test case the workomatic.rb file and all supporting files in the lib folder will be picked up.
