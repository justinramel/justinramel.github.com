---
comments: true
date: 2006-12-05 12:25:16
layout: post
slug: ruby-unit-testing-run-only-one-test
title: Ruby unit testing - run only one test
wordpress_id: 38
categories:
- Ruby
- Testing
---

If you don't wish to run all the unit tests in your test case you can tell ruby to run only one by passing in the name of the test:


    
    
      ruby test_mytestcase.rb --name test_just_this_method
    
