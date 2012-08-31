---
comments: true
date: 2007-05-17 10:41:24
layout: post
slug: monorail-nvelocity-how-to-find-out-if-your-in-the-first-item-of-a-foreach-loop
title: Monorail + NVelocity + How to find out if your in the first item of a foreach
  loop?
wordpress_id: 119
categories:
- MonoRail
---

A colleague needed to add a button to the first row of a table but how do you do this in a foreach loop?

NVelocity has a property called $velocityCount which you can check within the foreach loop:



    
    
    <span class="kwrd"><</span><span class="html">table</span><span class="kwrd">></span>
    #foreach($detail in $details)
      <span class="kwrd"><</span><span class="html">tr</span><span class="kwrd">></span>
        <span class="kwrd"><</span><span class="html">td</span><span class="kwrd">></span>
          $detail.ShortText)
          #if($velocityCount == 1) First Row! #end
        <span class="kwrd"></</span><span class="html">td</span><span class="kwrd">></span>
      <span class="kwrd"></</span><span class="html">tr</span><span class="kwrd">></span>
    #end
    <span class="kwrd"></</span><span class="html">table</span><span class="kwrd">></span>
