---
layout: post
title: "Monitoring your build"
date: 2013-01-14 22:28
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

Unless you're a glutton for punishment manually checking Jenkins after every
build is going to become very old very quickly. Luckily Jenkins has several
notification mechanisms to save you this manual task.

###Email Notification

We can setup Jenkins to send an email notification whenever a build fails this
save us having to check the server after every build, we can trust Jenkins to
email us on failure. Jenkins will also send a notification email when the build
returns to a working state.

Setting up email notification is a two-step process. First we give Jenkins
details of the email server and second we set which email addresses to notify
upon failure of a build.

###Email Server Configuration

Email server configuration is done via the Configure System page. You get to
the configuration page from the main Jenkins home page Manage Jenkins »
Configure System. At the bottom of this page is the E-mail Notification
section.

![email setup](/images/jenkins-net/ch08/email-setup.png)

Chances are you'll have a local SMTP server, if not you can use something like
the Gmail SMTP server as shown here. Make sure you tick the "Test configuration
by sending test e-mail" check box and then click the "Test Configuration"
button to have Jenkins send you a test email, confirming your configuration is
OK. Once you've successfully received an email don't forget to click the "Save"
button to save your changes.

###Project Notification Email

Once you have the email server configured you can specify per project who to
notify when a build fails. This is accessed via each Jobs configuration page,
for our Demo job we click Jenkins » Demo » Configure. At the bottom of this
page under the Post-Build Actions section is the E-mail Notification area.

![email notification](/images/jenkins-net/ch08/email-notification.png)

* Tick the "E-mail Notification" checkbox.
* Enter a space-separated list of email address to notify when a build fails.
* Tick the "Send e-mail for every unstable build" checkbox.

If you really want to annoy the person who broke the build you can send them
another email by ticking the "Send separate e-mails to individuals who broke
the build" checkbox.

Finally don't forget to click the "Save" button.

Unfortunately the only way to test this is working is to break the build,
follow the instructions in section 6. [Breaking the
build](/2013/01/14/breaking-the-build/) to test email notification is working.

###Your constant reminder

Email notification is great but I also like to have a constant reminder of the
current build status. The best way I have found to do this on Windows is by
using the Hudson Tray Tracker (read Jenkins Tray Tracker), which is available
to download from
[http://code.google.com/p/hudson-tray-tracker/](http://code.google.com/p/hudson-tray-tracker/).

![tray tracker 1](/images/jenkins-net/ch08/tray-1.png)

Once you download and install Hudson Tray Tracker you get a tray notification
icon showing a constant reminder of the current build status. Initially the
tray icon will be grey until you point it at a Jenkins build server.

![tray tracker 2](/images/jenkins-net/ch08/tray-2.png)

* Right click on the tray icon to access the context menu.

* Click Settings to configure the software.

![tray tracker 3](/images/jenkins-net/ch08/tray-3.png)

* Click the "Add server" button.

![tray tracker 4](/images/jenkins-net/ch08/tray-4.png)

* Enter the URL and port of your Jenkins server.

* Click the "OK" button.

You will now see a list of projects on the Jenkins server.

![tray tracker 5](/images/jenkins-net/ch08/tray-5.png)

Tick the Projects you would like to monitor. Here there is only our demo
project but in reality you may have lots of Projects to monitor.

![tray tracker 6](/images/jenkins-net/ch08/tray-6.png)

Once you have a server and projects setup, the tray icon will turn green to
indicate a good build. That is assuming you have a working build. When the
build breaks the icon will turn red and show a build failed message.

![tray tracker 7](/images/jenkins-net/ch08/tray-7.png)

You can also use the software to open Jenkins on the build page of a Job by
double clicking on the tray icon to open the list window.

![tray tracker 8](/images/jenkins-net/ch08/tray-8.png)

Then double click on the Job your interested in. In this case double clicking
on the Demo line will open up Jenkins on the Demo job page.

###The teams constant reminder

A large screen in the development room can be a great way to give everyone on
the team a highly visible, constant reminder of the current build status.

Jenkins has a Radiator View plugin that is designed specifically for this
purpose.

[https://wiki.jenkins-ci.org/display/JENKINS/Radiator+View+Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Radiator+View+Plugin)

![team](/images/jenkins-net/ch08/team.png)
