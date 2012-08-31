---
comments: true
date: 2009-01-09 14:28:01
layout: post
slug: monorail-custom-rescue-controller-irescuecontroller
title: MonoRail custom rescue controller (IRescueController)
wordpress_id: 127
categories:
- MonoRail
tags:
- MonoRail
---

##### The problem

 

I am calling a web service from a controller and the web service throws a WebException with different exception messages, one when the remote server is unavailable and another when the remote server times out. I’d like to show a rescue view based on the exception type **and** message not just it’s type.

 

The standard Monorail Rescue attribute only takes an exception type so there didn’t seem to be an easy way to solve my problem. I could have a generic rescue view which shows an error for all WebExceptions but I’d like to be a bit more specific. I could send all WebExceptions to the same rescue view and then handle the different messages in the view but I didn’t want the logic in my rescue view. 

 

I noticed in the trunk (revision 5407) the Rescue attribute takes a rescue controller which I’d never seen before. I started digging around the web and source and came up with the following solution which works although I not sure its the best solution!

 

##### My solution

 

I changed my base controller to use a rescue controller instead of rescue views:

 
    
    [Rescue(typeof(RescueController))]
    public class ApplicationController : SmartDispatcherController





I then created a RescueController:




    
    [Layout("default")]
    public class RescueController : SmartDispatcherController, IRescueController
    {
    	public void Rescue(Exception exception, IController controller, IControllerContext controllerContext)
    	{
    		SetRescueView("generalerror");
    		if (exception.GetType() == typeof(WebException) && exception.Message == "Unable to connect to the remote server") SetRescueView("webexception_cannot_connect");
    		if (exception.GetType() == typeof(WebException) && exception.Message == "The operation has timed out") SetRescueView("webexception_portal_timeout");
    
    	}
    
    	private void SetRescueView(string viewname)
    	{
    		RenderSharedView(Path.Combine("rescues", viewname));
    	}
    }





The Rescue method simply checks the exception type and message and if it gets a match it sets the relevant rescue view. Notice I’m using a little helper method to set the rescue view this tells Monorail look in the standard folder Views\rescues for the view otherwise it would be looking for these views in Views\Rescue which could get confusing.





##### Gotchas!






  
  * Make sure your custom rescue controller inherits from SmartDispatcherController otherwise your custom controller will not get called. See Castle Project Users list for [more detail](http://groups.google.co.uk/group/castle-project-users/browse_thread/thread/caab15edb9714ccc/5d8e5a96c309b42e)


  
  * Add the Layout attribute to the Rescue controller if you want to use your standard layout on the rescue pages.


  
  * If your using the Windsor container remember to add the Rescue controller to your container otherwise your custom rescue controller will not be found and called. This one had me scratching my head for a while!


  
  * Make sure your rescue views exist in the Views\rescues folder otherwise you will get the standard ASP.NET error page and it will look like none of this has worked.


  
  * This works with the trunk (revision 5407) not sure when the IRescueController functionality was added so it may not work with earlier revisions.





##### A better solution?





I thought a better solution would be to add a sub string message to the Rescue attribute which could be used to match the exception type and message. E.g:




    
    Rescue("web_exception_unable_to_connect", typeof(WebException), "Unable to connect to remote server")
    Rescue("web_exception_timeout", typeof(WebException), "The operation has timed out")





I couldn’t see an easy way to extend the standard Monorail rescue functionality so I ended up creating a builder which allowed me to define a map of exceptions to rescue views.




    
    builder.Map<WebException>()
    	.WithMessageContaining("Unable to connect to the remote server")
    	.OrMessageContaining("The remote server returned an error: (403) Forbidden.")
    	.ToRescue("webexception_cannot_connect");
    
    builder.Map<WebException>()
    	.WithMessageContaining("The operation has timed out")
    	.ToRescue("webexception_portal_timeout");





My final rescue controller simply uses the map to select the correct rescue view, no more if statements needed.




    
    [Layout("default")]
    public class RescueController : SmartDispatcherController, IRescueController
    {
    	private readonly IExceptionToRescueMapper _mapper;
    
    	public RescueController(IExceptionToRescueMapper mapper)
    	{
    		_mapper = mapper;
    	}
    
    	public void Rescue(Exception exception, IController controller, IControllerContext controllerContext)
    	{
    		SetRescueView(_mapper.GetRescueFor(exception));
    	}
    
    	private void SetRescueView(string viewname)
    	{
    		RenderSharedView(Path.Combine("rescues", viewname));
    	}
    }





If you know of a better way I’d love to hear it…
