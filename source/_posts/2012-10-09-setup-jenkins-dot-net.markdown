---
layout: post
title: "Setup Jenkins.NET"
date: 2012-10-09 20:35
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

There are some important settings, that we need to configure before we get
started building our first project.

## Manage

On the main Jenkins menu, click the 'Manage Jenkins' link.

![](/images/jenkins-net/ch03/03-00-manage.png)

You will now see the Manage Jenkins page. Click the 'Configure System' link to
get to the main configuration page.

![](/images/jenkins-net/ch03/03-00-manage-page.png)

## MSBuild

We need to setup MSBuild to carry out the compilation and build of your .NET
solutions. We can use any version of MSBuild you have installed on the Jenkins
machine. As Windows 7 comes with version 3.5 of the .NET Framework pre
installed I’ll demo that version here but obviously you can download, install
and use any version of the .NET Framework.

![](/images/jenkins-net/ch03/03-02-msbuild.png)

Click the 'Add MSBuild' button.

![](/images/jenkins-net/ch03/03-02-msbuild-2.png)

Set the name and path to MSBuild:

1. Name: v3.5
2. Path to MSBuild: C:\Windows\Microsoft.NET\Framework\v3.5\MSBuild.exe
3. Click the 'Save' button

In my next post we'll actually get to setup our first job!
