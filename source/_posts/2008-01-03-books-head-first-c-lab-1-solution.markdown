---
comments: true
date: 2008-01-03 21:52:00
layout: post
slug: books-head-first-c-lab-1-solution
title: Books + Head First C# + Lab 1 Solution
wordpress_id: 126
categories:
- BDD
- Books
tags:
- BDD
- Books
---

I've been reading through the new Head First book [Head First C#](http://www.amazon.com/gp/product/0596514824?ie=UTF8&tag=justinramelco-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0596514824)![](http://www.assoc-amazon.com/e/ir?t=justinramelco-20&l=as2&o=1&a=0596514824)
which appeared on [Safari](http://search.safaribooksonline.com/home) just before Christmas. I've been a fan of the Head Fist books ever since reading their best selling [Head First Design Patterns](http://www.amazon.com/gp/product/0596007124?ie=UTF8&tag=justinramelco-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0596007124)![](http://www.assoc-amazon.com/e/ir?t=justinramelco-20&l=as2&o=1&a=0596007124) book. This particular book is aimed at beginners / hobbyists so I'm not exactly the target audience but hey it covers C# 3 so its got to be worth at least a skim.

I was pleased to see they've added a new feature to the head first series namely lab sections. There are 3 lab sections in the book which are basically specifications for mini games, the idea being the reader creates the games using their newly acquired C# skills. I though this was a great idea and having a lot of spare time in front of my laptop over the Christmas (due to a very [sore ankle](http://justin.ramel.googlepages.com/ankle.jpg)) I did the first of the labs "A day at the races".

I used the lab as an exercise in [Behaviour Driven Development (BDD)](http://behaviour-driven.org/) which I'd recently read about [here](http://dannorth.net/introducing-bdd) and [here](http://codebetter.com/blogs/david_laribee/archive/2007/12/17/approaching-bdd.aspx). I also got to try out a Test Data Builder I'd read about [here](http://nat.truemesh.com/archives/000714.html). Now I'm not convinced I hit the nail on the head with the BDD as my solution wasn't created in a test behaviour first manor. This was mainly due to the fact the book provides you with the shell of a solution to keep things nice and simple for beginners. Never the less it was a good fun doing the lab it's a great way to try out new techniques.

All in all the BDD experience was pretty good not sure about the code duplication in the context setup but you got to love the way the descriptive contexts and method names combine to read like a sentence:

![](http://justin.ramel.googlepages.com/bdd.gif)

Also the Test Data Builder is a really flexible way to create test data using a fluent interface which again is really easy to read:

`myGuy = new GuyBuilder().WithName("Joe").AndCash(50).Build(); `

You can download the solution [here](http://justin.ramel.googlepages.com/lab01.zip).
