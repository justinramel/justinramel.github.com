---
comments: true
date: 2006-04-04 10:26:22
layout: post
slug: setting-up-ruby-on-rails
title: Setting up Ruby on Rails
wordpress_id: 51
categories:
- Ruby on Rails
---

I'm going to give Ruby on Rails (RoR) a try on my Windows XP machine.  Here's how I've set it up...





  1. Install Ruby
Using the [Ruby One Click Installer Ruby One Click Installer](http://rubyforge.org/projects/rubyinstaller/) (v184-16 release candidate 1)



  2. Setup proxy

    
    set HTTP_PROXY=http://wwwcache:8080




  3. GEM install Ruby on Rails

    
    gem install rails --include-dependencies




  4. Install RadRails
I also downloaded and installed the latest [RadRails](http://www.radrails.org/) (v0.6.1) 



  5. Database
I'm going to try rails with our dev MS-SQL server so no database to install. No doubt lots of configuring to do though!




#### NOTE:

There appears to be a problem with the WEBrick web server in this setup.  I couldn't find the answer on google but I did find a work around. If you run the WEBrick server using the standard ruby script\server you will get the following error:


    
    
    ruby script\server
    => Booting WEBrick...
    => Rails application started on http://0.0.0.0:3000
    => Ctrl-C to shutdown server; call with --help for options
    [2006-04-04 13:20:35] INFO  WEBrick 1.3.1
    [2006-04-04 13:20:35] INFO  ruby 1.8.4 (2005-12-24) [i386-mswin32]
    [2006-04-04 13:20:35] WARN  TCPServer Error: Bad file descriptor - bind(2)
    c:/ruby/lib/ruby/1.8/webrick/utils.rb:73:in `initialize': Bad file descriptor - bind(2) (Errno::EBADF)
            from c:/ruby/lib/ruby/1.8/webrick/utils.rb:73:in `create_listeners'
            from c:/ruby/lib/ruby/1.8/webrick/utils.rb:70:in `create_listeners'
            from c:/ruby/lib/ruby/1.8/webrick/server.rb:75:in `listen'
            from c:/ruby/lib/ruby/1.8/webrick/server.rb:63:in `initialize'
            from c:/ruby/lib/ruby/1.8/webrick/httpserver.rb:24:in `initialize'
            from c:/ruby/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/webrick_server.rb:59:in `dispatch'
            from c:/ruby/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/commands/servers/webrick.rb:59
            from c:/ruby/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
            from c:/ruby/lib/ruby/gems/1.8/gems/activesupport-1.3.0/lib/active_support/dependencies.rb:136:in `require'
            from c:/ruby/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/commands/server.rb:30
            from c:/ruby/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
            from c:/ruby/lib/ruby/gems/1.8/gems/activesupport-1.3.0/lib/active_support/dependencies.rb:136:in `require'
            from script/server:3
    



There appears to be some problem binding to the port 3000, netstat shows nothing running on port 3000 so I've no idea what is causing it. Any hoose a work around is simply to run on another port:


    
    
    ruby script\server --port=8000
    



If I do find out what is causing the problem I'll update this post.
