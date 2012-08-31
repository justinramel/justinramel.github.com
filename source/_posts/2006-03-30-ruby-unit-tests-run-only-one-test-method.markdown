---
comments: true
date: 2006-03-30 21:04:37
layout: post
slug: ruby-unit-tests-run-only-one-test-method
title: Ruby unit tests - run only one test method
wordpress_id: 39
categories:
- Ruby
- Testing
- Watir
---

What if you don't wish to run all the unit tests in your test case?

You can tell ruby to run only one test method by passing in the name of the test:


    
    
      ruby test_mytestcase.rb --name test_just_this_method
    
