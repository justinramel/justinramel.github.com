---
layout: post
title: "npm install - visual studio build tools problem"
date: 2014-01-11 13:58
comments: true
categories: javascript
---
Trying to install a node module on windows (via npm) and I keep getting the annoying error message:

```
error MSB8020: The build tools for Visual Studio 2010 (Platform Toolset = 'v100') cannot be found. To build using the v100 build tools, p lease install Visual Studio 2010 build tools.
```

I have Visual Studio 2013 installed but the project requires the 2010 version. After lots of digging around I discovered an option you can pass to npm, forcing it to use whatever version of Visual Studio you like.

`npm install karma --msvs_version=2013`

This was a welcome relief as getting the Visual Studio 2010 build tools appears to involve a full install of Visual Studio 2010!?!
