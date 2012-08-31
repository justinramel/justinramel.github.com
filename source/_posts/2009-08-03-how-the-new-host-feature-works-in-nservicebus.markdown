---
comments: true
date: 2009-08-03 17:02:24
layout: post
slug: how-the-new-host-feature-works-in-nservicebus
title: How the new Host feature works in nServiceBus
wordpress_id: 235
categories:
- nServiceBus
tags:
- nServiceBus
---

The latest _Alpha_ version of [nServiceBus](http://www.nservicebus.com/) uses the [TopShelf](http://code.google.com/p/topshelf/) project as part of its new hosting feature. This new Host feature makes it super easy to setup a console/windows service for your clients/servers. So here’s how *I think* it works and what you can do with it…

 

## Get nServiceBus

 

First you’ll need to get the latest build which includes the new Host feature either:

 

  
  * Check out the source and build it yourself from the [subversion](http://subversion.tigris.org/) repository:         
[https://nservicebus.svn.sourceforge.net/svnroot/nservicebus/trunk/](https://nservicebus.svn.sourceforge.net/svnroot/nservicebus/trunk/)         
OR 
   
  * Download a demo solution I hacked out of the nServiceBus samples (FullDuplex/RequestResponse): [nServiceBus Host Demo](http://cid-d7d57b78b0ddedf5.skydrive.live.com/browse.aspx/.Public/blog/nServiceBus)
 

Either way take a look at the FullDuplex/RequestResponse sample project which consists of a Client, Server and Messages project:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb.png)](http://justinram.files.wordpress.com/2009/08/image.png)

 

## Run the sample

 

**Note:** To get the Server to run successfully in my demo solution I had to change the app.config slightly by replacing the UnicastBusConfig setting with:

 

<UnicastBusConfig DistributorControlAddress="" DistributorDataAddress="">      
<MessageEndpointMappings>       
</MessageEndpointMappings>       
</UnicastBusConfig>

 

Ok simply hit F5 to run the sample and two console windows should appear one for the Client and one for the Server:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb1.png)](http://justinram.files.wordpress.com/2009/08/image1.png)

 

So everything is running ok our Client can send messages to the Server and receive a response. But what’s just happened? 

 

## Multiple startup projects

 

First the solution is set to start both the Client and the Server projects. This is set in the solution property pages you can view this setting by right clicking on the solution and selecting Set St_a_rtUp Projects…

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb2.png)](http://justinram.files.wordpress.com/2009/08/image2.png)

 

As you can see the solution is set to start multiple projects namely the Client and the Server.

 

Now the Server and Client projects are both Class Library’s so how come they are running as console apps when we F5 (debug) the solution? 

 

## Debug settings

 

If we take a look at the Debug settings for the Client (Right click the Client project and select P_r_operties, then Debug from the tab):

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb3.png)](http://justinram.files.wordpress.com/2009/08/image3.png)

 

Notice the Start Action is set to Start e_x_ternal program NServiceBus.Host.exe from the Client projects debug\bin directory. When we hit F5 to debug the application visual studio runs this exe and that’s how we get the console windows. 

 

## Reference NServiceBus.Host.exe

 

NServiceBus.Host.exe ends up in the debug\bin because its referenced by the project for example in the Client:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb4.png)](http://justinram.files.wordpress.com/2009/08/image4.png)

 

But how does it know where to get its configuration?

 

## Configuration

 

NServiceBus.Host.exe scans its current directory for any dlls. For each dll it finds it searches for a class which implements the interface IConfigureThisEndpoint. If the search is successful the Host knows to use the app.config for this dll so in the case of the Client – Client.dll.config is used to configure nServiceBus. 

 

## Client

 

If we take a look at the Client project we’ll find the class EndpointConfig which implements the IConfigureThisEndpoint. This is simply a marker interface which has no actual implementation. Notice there are other interfaces used to configure the client which do require implementations:

 

public class EndpointConfig:IConfigureThisEndpoint,      
As.aClient,   
ISpecify.ToUseXmlSerialization,       
ISpecify.XmlSerializationNamespace,       
IWantCustomInitialization,       
ISpecify.ToRun<ClientEndpoint>       
{       
public string Namespace       
{       
get { return "[http://www.UdiDahan.com";](http://www.UdiDahan.com";) }       
} 

 

public void Init(Configure configure)      
{       
configure.RijndaelEncryptionService();       
}       
} 

 

Of particular interest, the interface used to configure the dll as a client (As.aClient) and another to specify which code to actually run (ISpecify.ToRun<ClientEndpoint>). The ClientEndPoint class contains the code which is runs when the Host starts and stops.

 

Note there are lots more interfaces which can be used to specify configuration options:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb5.png)](http://justinram.files.wordpress.com/2009/08/image5.png)

 

## Server

 

The Server project works in pretty much the same way as the Client it has an EndpointConfig class:

 

public class EndpointConfig:IConfigureThisEndpoint,      
As.aServer,       
ISpecify.ToUseXmlSerialization,       


ISpecify.XmlSerializationNamespace,       
IWantCustomInitialization       
{       
public string Namespace       
{       
get { return "[http://www.UdiDahan.com";](http://www.UdiDahan.com";) }       
} 

 

public void Init(Configure configure)      
{       
configure.RijndaelEncryptionService();       
}       
} 

 

Here the interfaces are used to configure the dll as a server (As.aServer) and IWantCustomInitialization which allows you to specify additional configuration via the Init method. The Server project also contains the RequestDataMessageHandler class which the bus knows to use when a RequestDataMessage arrives.

 

All this makes it very easy to create Client and Server applications for nServiceBus which are a doddle to debug in visual studio.

 

But wait there's more…

 

## Run from console

 

You can run the Client or Server from outside Visual Studio from the command line. Open a command prompt, cd to the relevant bin folder and type: 

 

NServiceBus.Host.exe

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb6.png)](http://justinram.files.wordpress.com/2009/08/image6.png)

 

## Install as a Windows Service

 

We can install the Server as a Windows Service no extra code or configuration required! Open a command prompt, cd to the relevant bin folder and type:

 

NServiceBus.Host.exe /install

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb7.png)](http://justinram.files.wordpress.com/2009/08/image7.png)

 

You’ll then be prompted to supply some authentication details for the service:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb8.png)](http://justinram.files.wordpress.com/2009/08/image8.png)

 

Enter some relevant user details and hit ok and your service will be installed and ready to start:

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb11.png)](http://justinram.files.wordpress.com/2009/08/image11.png)

 

## Uninstall service

 

Finally you can also uninstall the service:

 

NServiceBus.Host.exe /uninstall

 

[![image](http://justinram.files.wordpress.com/2009/08/image_thumb10.png)](http://justinram.files.wordpress.com/2009/08/image10.png)

 

**Note:** The service will not disappear from this Services management console until you reboot your machine, this is standard for a windows service.

 

That’s as much as I have puzzled out for now, if I’ve made and glaring errors please let me know.


[![kick it on DotNetKicks.com](http://www.dotnetkicks.com/Services/Images/KickItImageGenerator.ashx?url=http%3a%2f%2fjustinram.wordpress.com%2f2009%2f08%2f03%2fhow-the-new-host-feature-works-in-nservicebus%2f&bgcolor=FF3300)](http://www.dotnetkicks.com/kick/?url=http%3a%2f%2fjustinram.wordpress.com%2f2009%2f08%2f03%2fhow-the-new-host-feature-works-in-nservicebus%2f)
