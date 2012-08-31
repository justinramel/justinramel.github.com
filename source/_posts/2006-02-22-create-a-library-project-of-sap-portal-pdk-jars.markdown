---
comments: true
date: 2006-02-22 15:53:00
layout: post
slug: create-a-library-project-of-sap-portal-pdk-jars
title: Create a library project of SAP Portal PDK JARs
wordpress_id: 8
categories:
- SAP Enterprise Portal
---

It is a good idea to create a library project which includes all the jar files needed for a portal project.  Why?
1. The SAP consultant told us to do it this way
2. It means on each new project you just need to include the library project and we are good to go.

So this is what we need to do:

**Step 1: Get the portal PDK JAR files**
These JAR files can de downloaded from the portal, they live under the following portal menu:

(Top Menu) Java Development -> (Left Sub Menu) Tools -> PDK Jars Download

Download the zip file and extract the JAR files to a folder on your PC for example c:\source\sap\devlibs

**Step 2: Create the library project**
In SAP Netweaver Developer Studio create a new project:

File -> New -> Project...

You will now see a wizard dialog:

Select Java -> Java Project

Click Next

Give the project a name DevLibs for example and specify a folder to save the project to.

You should now have a blank project to work with.

**Step 3: Import the SAP Portal PDK JAR files**
Right click your mouse on the new blank project you just created (in this case DevLibs) select Properties from the context menu.

You will now see the DevLibs properties dialog:
[![](http://photos1.blogger.com/blogger/752/2322/320/devlibs.0.jpg)](http://photos1.blogger.com/blogger/752/2322/1600/devlibs.0.jpg)
Select Java Build Path from the left pane.

Select "Libaries" from the Tab.

Click the "Add External JARs" button.

The file open dialog will now appear, select the downloaded JAR files from Step 1.

Click the "Order and Export" tab, click the "Select all" button.

Finally click the "OK" button.

You now have a library project which can be included in new portal projects!
