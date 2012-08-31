---
comments: true
date: 2009-04-30 18:29:37
layout: post
slug: developwithpassionbdd-notes
title: developwithpassion.bdd - notes
wordpress_id: 143
categories:
- BDD
tags:
- BDD
---

A few notes I’ve compiled while starting to play with [JP Boodhoo's](http://blog.jpboodhoo.com/) BDD framework ([http://github.com/developwithpassion](http://github.com/developwithpassion)). At first sight the syntax looks quite alien but try it for a while you eyes soon adjust. 

 

## JP blog posts 

 

  
  * [How I’m Currently Writing My BDD Style Tests – Part 1](http://blog.jpboodhoo.com/HowIrsquomCurrentlyWritingMyBDDStyleTestsNdashPart1.aspx)
   
  * [How I’m Currently Writing My BDD Style Tests – Part 2](http://blog.jpboodhoo.com/HowIrsquomCurrentlyWritingMyBDDStyleTestsNdashPart2.aspx)
   
  * [Test examples with MBUnit and jpboodhoo.bdd](http://blog.jpboodhoo.com/TestExamplesWithMBUnitAndJpboodhoobdd.aspx)
   
  * [Slight addition to jpboodhoo.bdd](http://blog.jpboodhoo.com/SlightAdditionToJpboodhoobdd.aspx)
   
  * [Using jpboodhoo.bdd with TestDriven.Net](http://blog.jpboodhoo.com/UsingJpboodhoobddWithTestDrivenNet.aspx)
   
  * [More new conventions for how I organize my tests!!](http://blog.jpboodhoo.com/MoreNewConventionsForHowIOrganizeMyTests.aspx)
 

## Base classes

 

  
  * observations_for_a_static_sut – For testing a static class or a quick inline test
   
  * observations_for_a_sut_with_a_contract – For testing against the interface of a class 
        
    * sut is automatically created 
     
    * No more broken test when you add a new dependency to a class! YAY
     
    * Automatic creation of sut can be over ridden
      
  * observations_for_a_sut_without_a_contract – For testing against a concrete class
 

## Delegate call order

 

  
  * context
        
    * Can define a context block in the concerns base class which will be run before a context block in the inheriting class
     
    * Can call method provide_a_basic_sut_constructor_argument
      
  * after_sut_has_been_initialized
   
  * because
   
  * it
   
  * after_each_observation
 

## Exceptions

 

When you want to <strike>test</strike> spec? for an exception use the doing method:

 

>   
> 
> because b = () =>        
doing(() => sut.MethodWhichThrows()); 
> 
>    
> 
> it should_throw_exception = () =>       
exception_thrown_by_the_sut.Message.should_contain("MY EXCEPTION"); 
