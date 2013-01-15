---
layout: post
title: "Jenkins.NET Breaking the build"
date: 2013-01-14 17:38
comments: true
categories: jenkins .net
---
{% render_partial _partials/jenkins.markdown %}

Lets break the build to see how Jenkins reacts. I'll add a DLL to the project
then "forget" to add it to source control; unfortunately I see this problem a
lot when new developers join the team.

### I see red projects

![](/images/jenkins-net/ch06/red-ball.png)

As you can see Jenkins now shows a red ball next to the Demo project. Also
notice the slightly cloudy weather icon indicating all is not well with our
project.

### How's the weather?

Jenkins uses a weather metaphor to show at a glance how a project is doing.

|![](/images/jenkins-net/ch06/weather-1.png)|No recent builds failed|
|![](/images/jenkins-net/ch06/weather-2.png)|1 out of the last 5 builds failed|
|![](/images/jenkins-net/ch06/weather-3.png)|2 out of the last 5 builds failed|
|![](/images/jenkins-net/ch06/weather-4.png)|3 out of the last 5 builds failed|
|![](/images/jenkins-net/ch06/weather-5.png)|4 out of the last 5 builds failed|
|![](/images/jenkins-net/ch06/weather-6.png)|5 out of the last 5 builds failed (Yeah I know the icon is no different to 4, go figure.)|


Obviously we want our projects to stay sunny and avoid the bad weather so next
time we'll discuss how to diagnose and fix a broken build.
