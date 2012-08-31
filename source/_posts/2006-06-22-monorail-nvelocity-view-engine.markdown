---
comments: true
date: 2006-06-22 11:08:05
layout: post
slug: monorail-nvelocity-view-engine
title: Castle Monorail - NVelocity View Engine
wordpress_id: 99
categories:
- MonoRail
---

I'm using the recommended view engine [NVelocity](http://www.castleproject.org/index.php/MonoRail:View_Engines_Book#NVelocity_View_Engine).

The following objects are available to the view code:
• context (IRailsEngineContext)
• request
• response
• session
• All entries in the request (if any)
• All entries in the Flash (if any)
• All entries in the PropertyBag (if any)

Also, a siteRoot string is added so you can build url definitions like:
`$siteRoot/home/index.rails
 <img src="$siteRoot/images/someimage.gif" />
`

**Notation (variable name): **

$ [ ! ][ { ][ a..z, A..Z ][ a..z, A..Z, 0..9, -, _ ][ } ]

Examples:




	
  * Normal notation: $mud-Slinger_9

	
  * Silent notation: $!mud-Slinger_9

	
  * Formal notation: ${mud-Slinger_9}




**Loops**
`#foreach($i in $items)
#each (this is optional since its the default section)
       text which appears for each item
#before
       text which appears before each item
#after
       text which appears after each item
#between
       text which appears between each two items
#odd
       text which appears for every other item, including the first
#even
       text which appears for every other item, starting with the second
#nodata
       Content rendered if $items evaluated to null or empty
#beforeall
       text which appears before the loop, only if there are items
       matching condition
#afterall
       text which appears after the loop, only of there are items
       matching condition
#end
`

**Binary expressions**
`#if($order.Status == "Undefined")
  Sorry, but we don't know this order.
#elseif($order.Status == "Created")
  Your order is being processed. Hold on!
#elseif($order.Status == "Dispatched")
  Your order has been dispatched through UPS. Cross your fingers!
#end
`

**IDictonary Parameters**
Calling a helper with IDictonary Paramaters:
`$HtmlHelper.SubmitButton("Login", $DictHelper.CreateDict("id=btnLogin"))`
