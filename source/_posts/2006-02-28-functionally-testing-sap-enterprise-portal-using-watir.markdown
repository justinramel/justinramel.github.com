---
comments: true
date: 2006-02-28 12:57:00
layout: post
slug: functionally-testing-sap-enterprise-portal-using-watir
title: Functionally testing SAP Enterprise Portal using Watir
wordpress_id: 14
categories:
- SAP Enterprise Portal
- Watir
---

It’s taken about a day but I’ve managed to get some functional tests running using Watir. It’s not been as easy as it could have been mainly due to the way the SAP Enterprise Portal uses iFrames and the anti cross site scripting in Internet Explorer. I got there in the end though! I can now logon to the portal and functionally test iViews using a fairly simple Watir (Ruby) script:

    
    <code>def logon
    $ie.goto($html_root)
    
    if $ie.contains_text("Log Off")
    logoff()
    end
    
    $ie.text_field(:id, 'logonuidfield').set($user_id)
    $ie.text_field(:id, 'logonpassfield').set($password)
    $ie.button(:name, 'uidPasswordLogon').click
    end</code>


A couple of things to note:

**Talk to the iView directly**
Due to the use of iFrames and IE anti cross site scripting accessing an iView which is embedded in a portal page is not possible with the current (1.4.1) version of Watir.  Simply get the url of the iView and access it directly.

**Problem with HTMLB Text Fields**
ID’s and Names of HTMLB Text Field controls appear to be generated on execution, so I had to write a little script which would find a text field using the title property:

    
    <code>def find_text_field_by_title(my_title)
    found_text_field = nil
    
    $ie.text_fields.each do |tf|
    if tf.title == my_title then
    found_text_field = tf
    break
    end
    end
    
    raise "No text field found with title = " +
    my_title if found_text_field.nil?
    
    return found_text_field
    end</code>


**NOTE: I’m sure my Ruby/Watir scripts leave a lot to be desired, I don’t really know who to code in Ruby but they do seem to work!**
