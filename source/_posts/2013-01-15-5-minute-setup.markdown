---
layout: post
title: "Jenkins for .net in 5 Minutes"
date: 2013-01-15 23:33
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

For my final post on using Jenkins with .net, here's how to do all that in 5
minutes!

###Install

1. Download the latest version of Jenkins from:
   [http://mirrors.jenkins-ci.org/windows/latest](http://mirrors.jenkins-ci.org/windows/latest)
2. Extract the setup files from the zip file.
3. Run the Setup.exe.
4. Accept all the defaults in the setup wizard.
5. Jenkins will now be installed and the main Jenkins page will be open.

###Add required .NET Plugins

1. Download and install your required .NET framework from:
   [http://www.microsoft.com/net/download](http://www.microsoft.com/net/download)
2. Open the Manage Plugins page, from the Jenkins menu select Jenkins » Manage
   Jenkins » Manage Plugins.
3. Click the "Available" tab.
4. Tick the "MSBuild" plugin.

###Add optional .NET Plugins

1. Tick the plugin for the source control management software your using.
2. If you want to run unit tests as part of your build Tick your chosen testing
   plugin, this guide will use NUnit.
3. Tick the "Active Directory Plugin" if you want to use Active Directory for
   Authentication.

###Setup Jenkins

1. Open the main setup page, from the Jenkins menu select Jenkins » Manage
   Jenkins » Configure System.
2. Under the MSBuild section, click the "Add MSBuild" button.
3. Set the name and path to MSBuild for example:
   Name: v3.5
   Path to MSBuild: C:\Windows\Microsoft.NET\Framework\v3.5\MSBuild.exe
4. Click the "Save" button.

###Setting up your first job

1. From the Jenkins menu click Jenkins » New Job.
2. Set Job name for example: Demo.
3. Select the “Build a free-style software project” radio button.
4. Then click the “OK” button.
5. Jenkins will now create the Job workspace on disk and redirect you to the
   job configuration page.

###Source Control

This guide will use Subversion but there are many available.

1. Under the Source Control Management section select the "Subversion" radio
   button.
2. Set the Repository URL for example:
   https://jenkins-net-demo.googlecode.com/svn/trunk

###Build Triggers

1. Under the Build Triggers section, tick the Poll SCM checkbox.
2. Enter "5 * * * *" in the Schedule text area, this translates to check for
   changes every 5 minutes.

###Build the Solution

1. Under the Build section click the "Add build step" button and select "Build
   a Visual Studio project or solution using MSBuild".
2. Set "MsBuild Version" to V3.5 (The version we setup previously)
3. Set "MsBuild Build File" to the name of the demo solution:
   Jenkins-net-demo.sln
4. Click the "Save" button and you'll be redirected to the Demo project page
5. Click the "Build Now" link.

You’re done!
