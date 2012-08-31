---
comments: true
date: 2009-06-10 17:15:59
layout: post
slug: resharper-format-settings
title: Resharper format settings
wordpress_id: 186
categories:
- Resharper
tags:
- Reshaper
---

I can never remember these so thought it best to write them down. Start with the settings from:

 

[http://codebetter.com/blogs/aaron.jensen/archive/2008/10/19/getting-resharper-and-vs-to-play-nice-with-mspec.aspx](http://codebetter.com/blogs/aaron.jensen/archive/2008/10/19/getting-resharper-and-vs-to-play-nice-with-mspec.aspx)

 

Plus a few extras…

 

Go to menu Resharper –> Options –> Languages –> C# –> Formatting Style

 

  
  * Braces Layout –> All set to (BSD style)
   
  * Braces Layout –> Empty braces formatting = Together on the same line[![image](http://justinram.files.wordpress.com/2009/06/image_thumb6.png)](http://justinram.files.wordpress.com/2009/06/image6.png)
   
  * Blank lines – I don’t like a lot of blank lines so I set mostly to 1/0[![image](http://justinram.files.wordpress.com/2009/06/image_thumb13.png)](http://justinram.files.wordpress.com/2009/06/image13.png)
   
  *     

Other –> Align Multiline Constructs – Call arguments = Off

  
   
  *     

Other –> Align Multiline Constructs – Expression = Off[![image](http://justinram.files.wordpress.com/2009/06/image_thumb14.png)](http://justinram.files.wordpress.com/2009/06/image14.png)

  
   
  *     

Other –> Other – Indent array, object and collection initializer block = Off[![image](http://justinram.files.wordpress.com/2009/06/image_thumb9.png)](http://justinram.files.wordpress.com/2009/06/image9.png)

  
 

## Regions

 

Stop Resharper adding regions to interface implementations and nested classes:

 

Go to menu: Resharper –> Options –> Languages –> C# –> Type Members Layout

 

Un-tick Use Default Patterns and you get a text area full of xml. Scroll to the bottom and delete the section:

 

<Group>     
<ImplementsInterface Immediate="true" Region="${ImplementsInterface} Members"/>      
</Group>

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb10.png)](http://justinram.files.wordpress.com/2009/06/image10.png)

 

Also delete the section:

 

<Group>     
<Name Region="Nested type: ${Name}"/>      
</Group>

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb11.png)](http://justinram.files.wordpress.com/2009/06/image11.png)

 

Finally click Ok.

 

 

 

 

 

 

 

## Code Cleanup

 

Go to menu Resharper –> Options –> Tools –> Code Cleanup

 

Add a new profile with the following settings:

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb12.png)](http://justinram.files.wordpress.com/2009/06/image12.png)

 

I didn’t realise I had fiddled with the default settings so much no wonder I can never remember them.
