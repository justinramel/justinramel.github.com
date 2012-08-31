---
comments: true
date: 2006-07-20 10:20:14
layout: post
slug: continuous-integration-cruisecontrolnet-subversion-msbuild-net-20
title: Continuous Integration + CruiseControl.Net + Subversion + MSBuild + .Net 2.0
wordpress_id: 101
categories:
- General
---

I’ve read quite a bit about [Continuous Integration](http://www.martinfowler.com/articles/continuousIntegration.html) and the .Net implementation [CruiseControl.Net](http://confluence.public.thoughtworks.org/display/CCNET). It always seemed like a really good idea but I’ve never gotten around to trying it out, until now…

By the way setting up the server was a lot easier than I thought it would be! Here’s what I did:



### CruiseControl.Net Setup


Download and run CruiseControl.Net setup
[
http://sourceforge.net/project/showfiles.php?group_id=71179&package_id=83198](http://sourceforge.net/project/showfiles.php?group_id=71179&package_id=83198)

I’ve used version 1.0.1:

[CruiseControl.NET-1.0.1-Setup.exe](http://prdownloads.sourceforge.net/ccnet/CruiseControl.NET-1.0.1-Setup.exe?download)


**NOTE:** After setup if your server has .Net 1.1 and 2.0 as mine did you may need to change the ccnet website to use .Net 2.0.  This can be done through the IIS control panel, get the properties of the ccnet site  and  change via the ASP.NET tab.



### Subversion Client


Your server will need the subversion console client on the server to allow CruiseControl to checkout your source.

[http://subversion.tigris.org/](http://subversion.tigris.org/)



### .Net 2 SDK


To allow us to build .Net 2  projects without the need for Visual Studio we need to download and install .Net 2 SDK onto  the server

[http://www.microsoft.com/downloads/details.aspx?familyid=fe6f2099-b7b4-4f47-a244-c96d69c35dec&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=fe6f2099-b7b4-4f47-a244-c96d69c35dec&displaylang=en)



### Setup MSBuild


To use MSBuild with CC.Net we need the logger dll -ThoughtWorks.CruiseControl.MsBuild.dll from:

[http://ccnetlive.thoughtworks.com/MSBuildXmlLogger%2DBuilds/](http://ccnetlive.thoughtworks.com/MSBuildXmlLogger%2DBuilds/)

Download and copy to:
C:\Program Files\CruiseControl.NET\webdashboard\bin\



### Directory structure


Setup your directory structure:

C:\CI\Myproject\
C:\CI\Myproject\build
C:\CI\Myproject\logs

Using your subversion client checkout source to C:\CI\MyProject\build



### ccnet.config


Add the project config to ccnet.confg:


    
    
    <cruisecontrol>
     <project name="MyProject">
      <!-- after a change is detected, wait 10 mins and then kick off the build-->
      <schedule type="schedule" sleepSeconds="600" />
      <!--set the sourcecontrol type to subversion and point to the subversion exe-->
      <sourcecontrol type="svn">
       <executable>C:\Program Files\Subversion\bin\svn.exe</executable>
       <workingDirectory>C:\CI\MyProject\build</workingDirectory>
       <trunkUrl>svn://svnserver/MyProject/trunk</trunkUrl>
       <autoGetSource>true</autoGetSource>
       <username>myuser</username>
       <password>mypassword</password>
      </sourcecontrol>
      <tasks>
       <!-- Configure MSBuild to compile the updated files -->c:\
       <msbuild>
        <executable>C:\windows\Microsoft.NET\Framework\v2.0.50727\MSBuild.exe</executable>
        <workingDirectory>C:\CI\MyProject\build\src\</workingDirectory>
        <projectFile>MyProject.sln</projectFile>
        <buildArgs>/noconsolelogger /p:Configuration=Debug</buildArgs>
        <targets></targets>
        <timeout>15</timeout>
        <logger>ThoughtWorks.CruiseControl.MsBuild.XmlLogger,C:\Program Files\CruiseControl.NET\webdashboard\bin\ThoughtWorks.CruiseControl.MsBuild.dll</logger>
       </msbuild>
      </tasks>
      <!--Publishers will be done after the build has completed-->
      <publishers>
       <xmllogger>
        <logDir>C:\CI\MyProject\Logs</logDir>
       </xmllogger>
      </publishers>
      <modificationDelaySeconds>10</modificationDelaySeconds>
     </project>
    </cruisecontrol>
    





### CC Tray



You will also want to install the CC Tray monitoring software on your pc:

[CCTray](http://prdownloads.sourceforge.net/ccnet/CruiseControl.NET-CCTray-1.0.1-Setup.exe?download)

It will allow you to keep an eye on the server from the comfort of your own pc.

That's it we're down!
