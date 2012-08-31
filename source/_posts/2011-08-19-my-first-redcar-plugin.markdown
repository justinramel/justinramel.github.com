---
comments: false
date: 2011-08-19 00:04:35
layout: post
slug: my-first-redcar-plugin
title: My first Redcar plugin
wordpress-id: 545
categories:
- General
- Ruby
tags:
- ruby
---
As a small thank you to the [Redcar](http://redcareditor.com/) team for such a great editor and in the spirit of giving a little bit back I'm documenting the process of creating my first plugin.

#### Introduction
I really like the idea of the [Redcar](http://redcareditor.com/) editor. Its written in Ruby, its possible to write your own plugins what's not to like? Though I must confess I don't use it as my day to day editor, I wonder if writing my own plugins will change that.

Let see how easy it is to write a plugin for [Redcar](http://redcareditor.com/).

#### What's da big idea
The idea for my first plugin is rather ambitious considering I've no idea how to write a plugin. I'd like to replicate some of the functionality of [Live Reload](http://livereload.com/) - basically refresh a browser web page whenever I save a file in Redcar. This will save me constantly hitting refresh in the browser when working with [Backbone.js](http://documentcloud.github.com/backbone/).

I'm hoping to trap the save event of [Redcar](http://redcareditor.com/) and call out to my browser (Chrome) and tell it to refresh the page.

#### Install Redcar
I first followed the install instructions:

[http://github.com/redcar/redcar/wiki/installation](http://github.com/redcar/redcar/wiki/installation)

All good no problems there (I'm running on a Mac OSX 10.7.1)

#### Plugin Guides
I then read the plugin guides I found here:

* [http://simplic.it/blog/my-first-redcar-plugin.html](http://simplic.it/blog/my-first-redcar-plugin.html)
* [http://quickwebdesign.net/documents/20110710_redcar_plugins.pdf](http://quickwebdesign.net/documents/20110710_redcar_plugins.pdf)

#### Plugin.rb
Setting up a plugin is really easy and well described in the guides listed above. Redcar itself is made up of a bunch of plugin's so there are no end of great examples to follow in the source code ([http://github.com/redcar/redcar](http://github.com/redcar/redcar))

For trapping the save event I dug into the source code and came across the method **project_refresh_task_type** which is called on all plugins after a save. To hook into this process my plugin simply defines the method:

``` ruby
def self.project_refresh_task_type
  RefreshBrowser
end
```

This may not be the best place to hook into save, Redcar has the concept of events and that may be a better place to look but for now this is working.

#### Browser refresh script
RefreshBrowser is a Redcar::Task which I have created to run the browser refresh script.

I managed to find a script to refresh the browser here:

[http://brettterpstra.com/watch-for-file-changes-and-refresh-your-browser-automatically/](http://brettterpstra.com/watch-for-file-changes-and-refresh-your-browser-automatically/)

The script uses a keyword to identify which tab to refresh in the browser so I needed this to be saved and configurable somewhere. Luckily Redcar has a storage mechanism built right in.

#### Storage
Redcar's storage mechanism allows you to easily store configuration data into a yaml file.

``` ruby
def storage
  @storage ||= Plugin::Storage.new('live_reload_plugin')
  @storage.set_default('keyword', '')
  @storage
end
```

Here I am using this mechanism to store the 'keyword' used by the RefreshBrowser task. This allows the user to edit the yaml file via the Redcar plugin preferences. It's also possible to setup a nice edit page but for now this will do.

#### Source
You can find the source for this plugin here:

[http://github.com/justinramel/redcar_plugin_live_reload](http://github.com/justinramel/redcar_plugin_live_reload)

#### Was it easy?
YES! The Redcar team have done a great job and made it incredibly easy to create your own plugins. In a couple of hours I made a useful plugin, useful to me at least. I've spent more time fussing over this blog post than developing the plugin.

So what you waiting for? Go give it a try!
