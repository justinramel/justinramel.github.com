---
comments: true
date: 2009-06-19 15:55:24
layout: post
slug: building-fubumvc-with-a-portable-version-of-rake
title: Building FubuMVC with a portable version of rake
wordpress_id: 207
categories:
- FubuMVC
- General
tags:
- FubuMVC
---

To build [FubuMVC](http://fubumvc.pbworks.com/) you need to install ruby, rake etc. Unfortunately for me the firewall at work will not allow me to get the rake gem (I’ve downloaded gems before using the HTTP_PROXY setting before but no luck this time). Any hoose I remember reading [Stephen Balkum](http://www.stephenbalkum.com/Default.aspx) post on packaging up [Rake](http://docs.rubyrake.org/index.html) as an executable.  I followed Stephens guide and created a portable rake package which got around my firewall problem **but** [FubuMVC](http://fubumvc.pbworks.com/) required another gem [rubyzip](http://rubyforge.org/frs/download.php/11376/rubyzip-0.9.1.zip) to allow a build.


## Adding another gem


Luckily using [Stephen’s guide](http://www.stephenbalkum.com/archive/2009/06/09/when-all-you-need-is-a-rake.aspx) its really easy to add extra gems, you just need to have them installed before you build your exe. So we follow the first part of the process outlined in [Stephen’s guide](http://www.stephenbalkum.com/archive/2009/06/09/when-all-you-need-is-a-rake.aspx) then do the following:

**NOTE:** In this case we need rubyzip but it could be any old gem.



	
  * Download [rubyzip](http://rubyforge.org/frs/download.php/11376/rubyzip-0.9.1.zip) and extract to contents to c:\rubywork\zip

	
  * To install rubyzip, at a command prompt in c:\rubywork\zip, run ..\ruby\bin\ruby install.rb

	
  * Download [zlib](http://www.zlib.net/zlib123-dll.zip) and extract the zlib1.dll to C:\rubywork\ruby\lib\ruby\1.8\i386-mswin32

	
  * Rename zlib1.dll to zlib.dll (rubyzip required this extra dll other gems may not)


Now continue part two of the process from [Stephen’s guide](http://www.stephenbalkum.com/archive/2009/06/09/when-all-you-need-is-a-rake.aspx) to compile your very own allinoneruby.exe which includes, rake and rubyzip.

You should now have allinoneruby.exe and rake.rb file.


## Building FubuMVC


We can now drop these files into to the FubuMVC project under the build support folder:

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb15.png)](http://justinram.files.wordpress.com/2009/06/image15.png)

We need a helper batch file in the root folder of FubuMVC called rake.bat which contains:

@.\build_support\allinoneruby.exe .\build_support\rake.rb %*

This will be called when we run the build.


## Run the build already


Drop to the command prompt and cd into the FubuMVC project root and simply type build. You should get something like:

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb16.png)](http://justinram.files.wordpress.com/2009/06/image16.png)


## Download


Don’t want to go through all that? You can download my version of portable rake [here](http://cid-d7d57b78b0ddedf5.skydrive.live.com/self.aspx/.Public/blog/portable|_rake/portablerake.zip) (_I don’t think I’m breaking any licensing agreements here, this is all open source software. If I am let me know and I’ll remove the link_)

**DISCLAIMER:** I offer no guarantees I can only confirm this works on my machine!


## One final note


I’ve used this method to build some of the other open source projects out there which use rake (_all the _[_cool kids_](http://blog.jpboodhoo.com/developwithpassionbdd.aspx)_ seem to be using rake_) and so far I’ve not had any problems. This could be pretty frictionless way to introduce rake to a team of .net developers who don’t want the overhead of installing ruby on their machines. Just add it to a tools folder check it in to source control they’ll never know!
