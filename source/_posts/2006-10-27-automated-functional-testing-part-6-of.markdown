---
comments: true
date: 2006-10-27 10:58:26
layout: post
slug: automated-functional-testing-part-6-of
title: SAP Enterprise Portal - Automated Functional Testing - Part 6 of ...
wordpress_id: 115
categories:
- SAP Enterprise Portal
- Testing
- Watir
---

Time for some more tips. I had a comment on my last post asking how to navigate around the portal so lets start there.  
  
**TOP TIP - How to navigate the portal**  
So how do you navigate around the portal using the menu? Simple you don't! I found there are lots of problems using the portal menus due to the number of frames used so I simply jump directly to the URL of the PAR file I am testing. Here is a typical test:  
`def test_typical  
# My Helper method which logs in using the given user id and password  
logon("myuserid", "mypassword")   
  
# Go directly to the URL of the PAR I want to test  
@ie.goto('http://portal:50000/irj/servlet/prt/portal/prtroot/uk.ac.ncl.testing.ISRPageProcessor')  
  
# do tests here  
end`  
Ok that's fine but how do you find the direct URL of the PAR file you want to test? Ahh thats were my next top tip comes in.  
  
**TOP TIP - How to find the direct URL of a PAR file**  
Open up the SAP Netweaver Developer Studio  
  
Open your project  
  
Open the file:  
`MyPortalProject  
dist  
PORTAL-INF  
Portalapp.xml`  
You should now see a "Run…" button for each portal component in your project  
  
Click the "Run…" button and the dev studio will open up a new browser window with the URL of your PAR file. Now simply use this URL in your test scripts.  
  
**COMING UP IN PART SEVEN**  
Short and sweet but at least I'm posting more often. Next time... You guessed it more top tips!
