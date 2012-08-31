---
comments: true
date: 2009-06-04 00:00:25
layout: post
slug: howto-add-svnexternals-in-windows-using-tortoisesvn
title: 'HOWTO: Add svn:externals in windows using tortoisesvn'
wordpress_id: 156
categories:
- Subversion
tags:
- Subversion
---

I have a few projects in subversion using the same set of third party tools nant, bdd, mbunit etc. I’ve read its a good idea to put the tools into their own repository and include them in the other projects using an svn:external. The advantage this gives you is any changes you make to the external repository can be updated easily across all projects. Any hoose this is who to do it. 

 

  
  1. Go to the root of the folder you want to add the externals too. 
   
  2. Right click on the root folder of the project you want to add the external repository to and select _T_ortoiseSVN –> _P_roperties.[![tortoise_settings[3]](http://justinram.files.wordpress.com/2009/06/tortoise_settings3_thumb.png)](http://justinram.files.wordpress.com/2009/06/tortoise_settings3.png) **Note:** This folder has to be a checked out subversion repository or you’ll not get the context menu!
   
  3. You will now see the subversion properties dialog.[![tortoise_properties[1]](http://justinram.files.wordpress.com/2009/06/tortoise_properties1_thumb.png)](http://justinram.files.wordpress.com/2009/06/tortoise_properties1.png)
   
  4. Click the _N_ew.. button. You will now see the Add properties dialog.[![tortoise_add_properties[1]](http://justinram.files.wordpress.com/2009/06/tortoise_add_properties1_thumb.png)](http://justinram.files.wordpress.com/2009/06/tortoise_add_properties1.png)
   
  5. Select svn:externals from the property name drop down list. 
   
  6. Enter the name you want to give to the external folder followed by the path to your tools repository in property value text area.        
In the example above: tools svn://server/tools/trunk         
**Note:** You can add more external repositories by simply adding more lines to the property value text area. 
   
  7. Click Ok to add the property will now be listed in the properties dialog.[![tortoise_properties2[1]](http://justinram.files.wordpress.com/2009/06/tortoise_properties21_thumb.png)](http://justinram.files.wordpress.com/2009/06/tortoise_properties21.png)
   
  8. Right click on the root folder and select SVN Update from the menu. Subversion will now pull down the files from the external repository and your done. 
 

Once you check this change in other people checking out from the repository will automatically get the externals folder. Also any changes to the external repository will be updated in this repository on any update. So in this case if I add a new tool or update one of the tools all repositories using this external repository will get the changes on their next update. 

 

### Gotchas

 

  
  * Don't forget to give the folder name before the repository address and not just the repository address or you will get an error along the lines of: Error parsing svn:externals property on …![tortoise_error[1]](http://justinram.files.wordpress.com/2009/06/tortoise_error1_thumb.png)
