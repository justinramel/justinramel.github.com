---
layout: post
title: "Jenkins.NET"
date: 2012-09-17 21:58
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

## Introduction

This is the first in a series of posts which I’ll be writing on using Jenkins
to build .NET solutions. These posts will be as detailed as possible, probably
too detailed in places.

## Installing Jenkins

> **NOTE:** Jenkins used to be known as 'Hudson' but when Oracle bought Sun there
> was a fall out between the then 'Hudson' developers and Oracle so they decided
> to fork the project and rename themselves Jenkins. [Full details](http://jenkins-ci.org/content/hudsons-future)

I'm going to install and setup Jenkins on a freshly minted Windows 7 virtual
machine although this process should work fine on other versions of Windows.

Go to the Jenkins home page: [http://jenkins-ci.org/](http://jenkins-ci.org/)

[![](/images/jenkins-net/ch01/01-00-jenkins-home-page.png)](http://jenkins-ci.org/)

### Download

Rather than the generic .war file we'll download the Windows native package,
which saves as a few steps during installation. The latest windows package is
available here:

[http://mirrors.jenkins-ci.org/windows/latest](http://mirrors.jenkins-ci.org/windows/latest)

![](/images/jenkins-net/ch01/01-01-download.png)

I'm using Internet Explorer here, which by default blocks the installer from
downloading. Notice the warning message shown at the top of the browser
window.

![](/images/jenkins-net/ch01/01-01-warning.png)

Click the message bar to get the download options context menu.

![](/images/jenkins-net/ch01/01-01-context-menu.png)

Select the Download File… menu option. You will now see the File Download
dialog.

![](/images/jenkins-net/ch01/01-01-file-download-dialog.png)

Click the Save button to download the installation zip file to your download
folder. You will now see the Save As dialog again click the Save button to
actually download the file.

![](/images/jenkins-net/ch01/01-01-save-as-dialog.png)

In a short while you will see the Download complete dialog. Click the Open
button to open the zipped installation file.

![](/images/jenkins-net/ch01/01-01-download-complete.png)

Internet Explorer Security may kick in and ask if you want to allow this
operation. Click the Allow button to open the zip file.

![](/images/jenkins-net/ch01/01-01-ie-security.png)

Once the zip file is open, Click Extract all files from the menu.

![](/images/jenkins-net/ch01/01-01-open-zip.png)

You will now see the Extract zip file dialog, Click the Extract button to
extract the files to the default location.

![](/images/jenkins-net/ch01/01-01-zip-extract-dialog.png)

Phew! That's the download complete.

### Setup

Finally we can run the Setup program. Double click setup to run the program.

![](/images/jenkins-net/ch01/01-02-setup.png)

Windows will show a Security Warning to make sure you trust the publisher of
this software. Click Run to begin the installation.

![](/images/jenkins-net/ch01/01-02-warning.png)

You will now see the Jenkins installation wizard. Click the Next button.

![](/images/jenkins-net/ch01/01-02-wizard-1.png)

The wizard allows you to change the installation folder. Click Next to accept
the default folder.

![](/images/jenkins-net/ch01/01-02-wizard-2.png)

You are now at the final page of the setup wizard. Click the Install button
and the installation will begin.

![](/images/jenkins-net/ch01/01-02-wizard-3.png)

On Windows 7 the User Account Control may kick in to ask permission to run the
installation. Click the Yes button to continue.

![](/images/jenkins-net/ch01/01-02-user-access-control.png)

The installation wizard will now copy Jenkins onto your machine and display a
message upon completion. Click the Finish button.

![](/images/jenkins-net/ch01/01-02-wizard-complete.png)

The install wizard will now open the Jenkins web page.

![](/images/jenkins-net/ch01/01-02-jenkins.png)

Congratulation Jenkins is now installed on your machine!
