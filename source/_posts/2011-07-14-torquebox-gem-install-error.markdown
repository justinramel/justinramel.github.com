---
comments: false
date: 2011-07-14 11:42:27
layout: post
slug: torquebox-gem-install-error
title: TorqueBox - gem install error
wordpress_id: 546
categories:
- torquebox
---

#### TorqueBox Install


I'm playing with latest version of TorqueBox ([Currently 2.x.incremental.245](http://torquebox.org/2x/builds/)) the easiest way to install it is via a gem:

`gem install torquebox-server --pre --source http://torquebox.org/2x/builds/LATEST/gem-repo/`

Full details on the TorqueBox blog ([http://torquebox.org/news/2011/06/10/torquebox-gem/](http://torquebox.org/news/2011/06/10/torquebox-gem/)).



#### Error


Anyhoose when doing the gem install on my dev server (CentOS 5.6) I got the error:

Error: Your application used more memory than the safety cap of 500m.
Specify -J-Xmx####m to increase it (#### = cap size in MB).



#### Fix


After a bit digging around it turns out you need to set the heap size when running the gem install:

`jruby -J-Xmx900m -S gem install torquebox-server --pre --source http://torquebox.org/2x/builds/LATEST/gem-repo/`

More details on [stackoverflow](http://stackoverflow.com/questions/1758374/error-your-application-used-more-memory-than-the-safety-cap-of-500m-specify-j).

Hope that helps someone or maybe me if have to do this again!
