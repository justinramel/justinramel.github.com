---
comments: true
date: 2006-12-05 14:42:36
layout: post
slug: sap-enterprise-portal-automated-functional-testing-part-7-of
title: SAP Enterprise Portal + Automated Functional Testing - Part 7 of ...
wordpress_id: 118
categories:
- SAP Enterprise Portal
- Testing
- Watir
---

In anticipation of posting about a new topic I'm going to wrap up my Watir Automated testing posts with a few more top tips.

**TOP TIP - How do I run a single test?**

So you have lots of tests in your test suite but only want to run one? No need to create an ad-hoc test case, simply pass in the **--name** parameter when running the test:

`ruby test_mytestcase.rb --name test_just_this_method`

**TOP TIP - How do I run the test in background mode?**

Running the test so you can see what is going on in the browser is sometimes useful but most of the time you'll want to run the tests in the background and just see the results. This is easily done by passing the **-b** parameter on the command line:

`ruby test_mytestcase.rb -b`

**TOP TIP - Helper methods**

I have a couple of helper methods which I use in most of my test cases:
`
def should_find(find_me)
  assert(@ie.contains_text(find_me), "*\n*\n*\nText not found: #{find_me}\n*\n*\n*")
end

def should_not_find(find_me)
  assert_nil(@ie.contains_text(find_me), "*\n*\n*\nFound text which should not be present: #{find_me}\n*\n*\n*")
end
`
No clever code here it just means I can write tests which are easier to read:
`
should_not_find("Portal Runtime Error")
should_find("Success")
`
**FIN**
Well I'm running out of content about testing as you can probably tell! So I guess thats a wrap. I'll no doubt re-visit automated testing again at some point but for now thats my lot.

**NEXT TIME**
I've been working on creating web services for Enterprise Portal and calling those web services from Microsoft .Net. I've taken lots of notes, so expect a series of EP web services posts real soon.
