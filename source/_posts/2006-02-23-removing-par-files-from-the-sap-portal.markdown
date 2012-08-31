---
comments: true
date: 2006-02-23 11:34:00
layout: post
slug: removing-par-files-from-the-sap-portal
title: Removing PAR files from the SAP Portal
wordpress_id: 10
categories:
- SAP Enterprise Portal
---

So you've accidentally uploaded a PAR file to the portal eh?

Here's how to get rid...

(Top Menu) Java Development -> (Left Sub Menu) Tools -> Portal Archive Deployer&Remover

(Main Page) Archive Remover

Select the PAR file you wish to remove from the drop down list and click the "Clean" button

You should now see a message along the lines of:

INFO: Received clean-up request for application: "MyApp"
INFO: MyApp has been successfully removed from the PCD.

The PAR is no more.
