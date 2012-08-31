---
comments: true
date: 2006-10-18 11:13:13
layout: post
slug: sap-enterprise-portal-functional-testing-part-5-of
title: SAP Enterprise Portal - Automated Functional Testing - Part 5 of ...
wordpress_id: 113
categories:
- SAP Enterprise Portal
- Testing
- Watir
---

Ok last time I promised some hints and tips so lets begin. I'm going to keep the hints and tips posts fairly short in the hope it will encourage me to post more often. I received a comment on my last post asking how I find the ID/Name attributes of my forms so I though that would be a good place to start.  
  
**TOP TIP - How to find ID/Name attributes of a form  
**To save me having to sifting through the html code of a page for the ID/Name of a control I use the [FireFox](http://www.mozilla.com/firefox/) browser with the [Web Developer Toolbar](https://addons.mozilla.org/firefox/60/) extension installed. The [Web Developer Toolbar](https://addons.mozilla.org/firefox/60/) is a great time saver not only for finding out form details but it has lots of other features too, I strongly recommend you check it out.  
  
When you have the [Web Developer Toolbar](https://addons.mozilla.org/firefox/60/) installed under the **Forms menu** you have the **Display Form Details** option, simply select this option and the page will be highlighted with yellow tags showing the ID/Name attributes of each item on the form.  
  
**NOTE:** Forms items which are created using HTMLB do not get a static ID/Name attribute these attributes appear to be generated each time the page is created. If this is the case how do we write tests against HTMLB forms? That's were the next top tip comes in...  
  
**TOP TIP - Writing Watir test against HTMLB forms**  
As I mentioned above HTMLB forms do not have a static ID/Name attribute, they are generated each time the page is created so you will find your HTMLB form controls will have an ID/Name of something along the lines of "htmlb_18528_htmlb_9998_3" if you then reload the page the ID/Name attributes will have changed i.e. "htmlb_18328_htmlb_9991_1". This means the following Watir test code would not work as each time the page reloaded the _:id_ attribute would be different.  
  
`@ie.text_field(:id, 'htmlb_18528_htmlb_9998_3').set('test me')`  
  
So how do we get around this? Well the best way I have found is to use Watir's _:index_ parameter when accessing form controls. The _:index_ parameter works by sequentially counting form controls from left to right top to bottom. So to set the text of the second control on the page we use the following code:  
  
`@ie.text_field(:index, 2).set('test me')`  
  
This is not an ideal solution due to the fact if you change the layout of the page your index's will also change and break your tests. However I've been using this method for a while now and it's never been a major problem, besides I'm not sure how else it could be done!  
  
**COMING UP IN PART SIX**  
Well that post turned out to be slightly longer than I planned, so much for keeping these tips short. Next time more of the same.
