---
comments: true
date: 2007-06-18 17:03:34
layout: post
slug: castle-using-the-trunk-my-config
title: Castle + Using the Trunk + My registry entries
wordpress_id: 122
categories:
- Castle
tags:
- Castle
---

When I build from the trunk I usually follow the instructions found here:

[http://using.castleproject.org/display/CASTLE/Using+the+Trunk](http://using.castleproject.org/display/CASTLE/Using+the+Trunk)

My source location is slightly different from the instructions so I have to hand edit the registry entries listed at the end of the page. So to save me doing that again here they are:

`Windows Registry Editor Version 5.00 [HKEY_LOCAL_MACHINE\SOFTWARE\Castle] "vs8templatelocation"="C:\\source\\Castle\\Tools\\VSNetWizards\\CastleTemplates\\VS8" [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727\AssemblyFoldersEx\castle] @="C:\\source\\Castle\\build\\net-2.0\\debug" `
