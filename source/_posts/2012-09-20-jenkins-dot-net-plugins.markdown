---
layout: post
title: "Jenkins.NET Plugins"
date: 2012-09-20 18:43
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}
## Plugins

To compile .NET and run our tests we need to add a few plugins to Jenkins.
Thankfully Jenkins makes is very easy to find and install plugins. On the main
Jenkins menu click the 'Manage Jenkins' link.

![](/images/jenkins-net/ch02/02-00-manage-jenkins-menu.png)

You will now see the Manage Jenkins page. Click the 'Manage Plugins' link.

![](/images/jenkins-net/ch02/02-00-manage-jenkins-page.png)

You will now see a list of the currently installed plugins. Click the
Available tab to see a list of all the Jenkins plugins, which are available to
install.

![](/images/jenkins-net/ch02/02-00-plugin-manager.png)

As you can see Jenkins has a massive number of plugins. I encourage you to
look through and play with the plugins they are really useful and the list is
growing by the day.

![](/images/jenkins-net/ch02/02-00-available-plugins.png)

## Required Plugins

Without these required Plugins you will not be able to build and test .NET
solutions. So you must at least install these Plugins for the rest of this
guide to work.

### Build Plugins

The Build Plugin we’ll be using is MSBuild this allows us to build a .NET
solution.

* **MSBuild Plugin** - _This plugin allows you to use MSBuild to build .NET
  projects._

### Testing Plugins

You'll need one of these depending on your chosen test framework.

* **MSTest Plugin** - _This plugin converts MSTest TRX test reports into JUnit
  XML reports so it can be integrated with Jenkins JUnit features._
* **NUnit Plugin** - _This plugin allows you to publish NUnit test results._
* **xUnit Plugin** - _This plugin makes it possible to publish the test results
  of an execution of a testing tool in Jenkins._
* **Gallio Plugin** - _This plugin makes it possible to publish Gallio/MbUnit
  test results._

Tick the check box next to each of the required Plugins and then click the
'Download now and install after restart' button.

![](/images/jenkins-net/ch02/02-00-installing-plugins.png)

### Optional Plugins

These Plugins are optional but still recommend ranging from genuine
productivity tools to just plain fun.


### Jenkins Enhancements

* **Green Balls** - _Changes Hudson to use green balls instead of blue for
  successful builds. **Who doesn't want Green Balls!**_
* **Copy project link plugin** - _This plugin adds the "Copy project" link into
  left side panel in the main project page._
* **Radiator View Plugin** - _Provides a job view displaying project status in
  a highly visible manner. This is ideal for displaying on a screen on the
  office wall as a form of Extreme Feedback Device._

### Authentication

* **Active Directory Plugin** - _With this plugin, you can configure Jenkins
  authenticates the username and the password through Active Directory._

> **NOTE:** You can setup Authentication up without Active Directory but I’m
> guessing most of you already login via Active Directory so this Plugin saves
> you having to remember yet another password.

### Code Analysis

* **Task Scanner Plugin** - _This plugin scans the workspace files for open
  tasks and generates a trend report._
* **Warnings Plugin** - _This plugin generates the trend report for compiler
  warnings in the console log or in log files._

### Build Tools

* **NAnt Plugin** - _This plugin allows for the execution of a NAnt build as a
  build step._
* **PowerShell Plugin** - _Integrates with Windows PowerShell._

### Fun, Fun, Fun

* **ChuckNorris Plugin** - _Displays a picture of Chuck Norris (instead of
  Jenkins the butler) and a random Chuck Norris 'The Programmer' fact on each
  build page. **Every build server needs a Chuck Norris, right?**_
* **The Continuous Integration Game plugin** - _This plugin introduces a game
  where users get points on improving the builds. Although this is indeed a fun
  plugin it can help when first introducing Jenkins to your team, a little
  healthy competition never did anyone any harm._
