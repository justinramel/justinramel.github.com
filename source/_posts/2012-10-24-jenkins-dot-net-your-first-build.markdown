---
layout: post
title: "Jenkins.NET Your first build"
date: 2012-10-24 21:11
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

From the Project Demo page we created last time we can activate a Build at
will.

### Build Now

![](/images/jenkins-net/ch05/build-now.png)

Click the “Build Now” link.

This tells Jenkins to build the Job we have just defined.

### Build History

![](/images/jenkins-net/ch05/build-history-1.png)

The Build History will show the Job running. Once the build is complete you
should have your first successful build.

![](/images/jenkins-net/ch05/build-history-2.png)

Clicking the Build History link (in this case 19-Feb-2012 00:10:39) will take
you to the build page for the Demo Job.

### Console Output

This page allows us to access all the information relevant to the build we just
ran. The area we are interested in is the Console Output this shows all the
programs that ran during the build.

![](/images/jenkins-net/ch05/console-output-1.png)

Click the “Console Output” link.

![](/images/jenkins-net/ch05/console-output-2.png)

This is the place to come whenever you are trying to debug a failing build.
Everything you need to fix the problem will usually be shown on this page.

As you can see this was a successful build and we can see that:

* Jenkins created a workspace for the Job
* Ran a Subversion check out
  * Listed of all files updated
* Ran MSBuild
  * Shows all output from MSBuild
* Shows Success message
