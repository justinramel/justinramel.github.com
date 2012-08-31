---
comments: true
date: 2009-06-08 14:33:21
layout: post
slug: setup-asp-net-mvc-with-spark-view-engine-in-5-minutes-or-less
title: Setup ASP.NET MVC with Spark View Engine in 5 minutes or less
wordpress_id: 171
categories:
- Mvc
- Spark
tags:
- aspnetmvc
- Spark
---

Setup folder structure:

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb.png)](http://justinram.files.wordpress.com/2009/06/image.png)

 

Download and put the [asp.net mvc](http://www.asp.net/mvc/download/) dll’s in mvc folder and [spark](http://sparkviewengine.codeplex.com/Release/ProjectReleases.aspx?ReleaseId=27109) dll’s in spark folder. 

 

Create a new asp.net application not a **mvc** application just a standard asp.net application. This means you will not get the mvc helpers for creating controllers and views but that’s not a massive loss and has the advantage that you don’t need the asp.net mvc installed if you open the solution on another machine.

 

[![add new project](http://justinram.files.wordpress.com/2009/06/image_thumb1.png)](http://justinram.files.wordpress.com/2009/06/image1.png)Change content of Default.aspx to: <!-- Placeholder do not delete! -->

 

The default.aspx placeholder is required to allow the asp.net routing to work. 

 

Delete the code behind files for Default.aspx (Default.aspx.cs, Default.aspx.designer.cs) they are not needed.

 

Add references to the Spark.dll and Spark.Web.Mvc.dll located in the libs folder.

 

[![vs_add_ref](http://justinram.files.wordpress.com/2009/06/vs_add_ref_thumb.png)](http://justinram.files.wordpress.com/2009/06/vs_add_ref.png)

 

 

Add references to asp.net mvc System.Web.Routing.dll, System.Web.Abstractions.dll, System.Web.Mvc.dll

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb2.png)](http://justinram.files.wordpress.com/2009/06/image2.png)

 

Add spark to the web.config:

 

</sectionGroup>      
<section name="spark" type="Spark.Configuration.SparkSectionHandler, Spark"/>       
</configSections>

 

<spark>      
<compilation debug="true" />       
</spark>

 

Debug true shows compilation errors when rendering views.

 

Add routing to httpModules section of web.config:

 

<add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web.Routing, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"/>

 

Add a application.cs which creates the routes and registers the spark view engine:

 

using System.Collections.Generic;      
using System.Web.Mvc;       
using System.Web.Routing;       
using Spark.Web.Mvc; 

 

namespace Web      
{       
public class Application       
{       
public void RegisterRoutes(IList<RouteBase> routes)       
{       
routes.Add(new Route(       
"{controller}/{action}/{id}",       
new RouteValueDictionary(new {controller = "home", action = "index", id = ""}),       
new MvcRouteHandler()));       
} 

 

public void RegisterViewEngine(IList<IViewEngine> engines)      
{       
SparkEngineStarter.RegisterViewEngine(engines);       
}       
}       
}

 

Add a global.asax with the following code behind.

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb3.png)](http://justinram.files.wordpress.com/2009/06/image3.png)

 

using System;      
using System.Web;       
using System.Web.Mvc;       
using System.Web.Routing; 

 

namespace Web      
{       
public class Global : HttpApplication       
{       
protected void Application_Start(object sender, EventArgs e)       
{       
var app = new Application();       
app.RegisterRoutes(RouteTable.Routes);       
app.RegisterViewEngine(ViewEngines.Engines);       
} 

 

protected void Application_BeginRequest(object sender, EventArgs e)      
{       
string path = Request.AppRelativeCurrentExecutionFilePath;       
if (string.Equals(path, "~/default.aspx", StringComparison.InvariantCultureIgnoreCase) ||       
string.Equals(path, "~/"))       
{       
Context.RewritePath("~/Home");       
}       
}       
}       
}

 

Create content, controllers and view folders in the root of the asp.net project:

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb4.png)](http://justinram.files.wordpress.com/2009/06/image4.png)

 

Create a shared folder in the views folder with a _global.spark file this will be used to share come code with all views.

 

<use namespace="System.Collections.Generic"/>      
<use namespace="System.Web.Mvc.Html"/>

 

Create a layouts folder in the views folder with a file called application.spark which will be used for the layout of the application very much like a master page.

 

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "[http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"](http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd")>       
<html xmlns="[http://www.w3.org/1999/xhtml"](http://www.w3.org/1999/xhtml")>       

<head>       
<title>Sample</title>       
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />       
</head>       
<body>       
<h1>Header</h1>       
** <use content="view"/>        
** <h1>Footer</h1>       
</body>       
</html>

 

The use content view tag highlighted above is replaced by the current view returned by asp.net mvc.

 

Add a HomeController.cs under the controllers folder with the following content:

 

using System.Web.Mvc; 

 

namespace Web.controllers      
{       
public class HomeController : Controller       
{       
public ActionResult Index()       
{       
return View();       
}       
}       
}

 

Under the views folder create a home\index.spark with the following content:

 

<p>Hello spark.</p>

 

Run the project and you should get:

 

[![image](http://justinram.files.wordpress.com/2009/06/image_thumb5.png)](http://justinram.files.wordpress.com/2009/06/image5.png)

 

 

 

 

 

 

 

You can download this sample solution [here](http://fppuvw.bay.livefilestore.com/y1puB8Efa8gk4G6CzMEi40m1JxymO-5kxvTnYWbZ3uh1YZD71y8xOd58vSLWuNpPG06X9y7MgTOntrkvH82-jAqoMWnN9ranxJ6/sparksetup.zip?download).
