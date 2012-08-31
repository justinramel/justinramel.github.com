---
comments: true
date: 2006-06-29 13:34:23
layout: post
slug: monorail-%e2%80%93-moving-from-beta5-to-latest-build
title: Castle Monorail – Moving from Beta5 to latest build
wordpress_id: 100
categories:
- MonoRail
---

I’ve decided to move my "toy" MonoRail project from the Beta 5 version to the latest build so I can have a play with the new features. Mostly Formhelper!

Moving to the latest build broke a few things in my solution:



### The Build


**Nunit framework**

My web test project was using Nunit version 2.2.0.0. Which is used by Castle.MonoRail.TestSupport I believe although don't quote me on that I could be wrong. Any who it now requires the latest version of the nunit.framework.dll (2.2.8.0). I change the reference and all was well.

**DataBindAttribute**
Next up was the DataBindAttribute which appears to have changs slightly. I did have:

`public void LoginSubmit([DataBind(Prefix = "student")] Student student)`

It appears the **Prefix** parameter is now explicit, a simple change:

`public void LoginSubmit([DataBind("student")] Student student)`



### The Tests


Ok now my solution builds but all of my ActiveRecord unit tests fail. I get the following error:

`TestFixture failed: You can't invoke ActiveRecordStarter.Initialize more than once`

Turns out to be a problem in the InitFramework method of my AbstractModelTestCase class. Initalialze is being called twice:

`protected virtual void InitFramework()
{
  IConfigurationSource source = ConfigurationManager.GetSection("activerecord") as IConfigurationSource;

  ActiveRecordStarter.Initialize(source);

  ActiveRecordStarter.Initialize( source, typeof(Student), typeof(LoginAudit) );
}`

I guess there is now no need for the first **ActiveRecordStarter.Initialize(source);** call so I remove it and all is well!



### The Run


Ok now my solution builds and passes the test but all is not well at run time I get the following error:

`Looks like you forgot to register the http module Castle.MonoRail.Framework.EngineContextModule
Add '<add name="monorail" type="Castle.MonoRail.Framework.EngineContextModule, Castle.MonoRail.Framework" />' to the <httpModules> section on your web.config`

This is a breaking change mentioned in the release notes and you must update your web.config. But don’t get your httpModules and your httpHandlers mixed up as I did. Simply add the httpModules to your web.config:

`<system.web>
  <httpHandlers>
		<add verb="*" path="*.aspx" type="Castle.MonoRail.Framework.MonoRailHttpHandlerFactory, Castle.MonoRail.Framework"  />
  </httpHandlers>
  <httpModules>
		<add name="monorail" type="Castle.MonoRail.Framework.EngineContextModule, Castle.MonoRail.Framework" />
	</httpModules>
</system.web>
`



### The End


That’s it we’re down! Now I get to play with the latest version.
