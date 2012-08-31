---
comments: true
date: 2006-03-16 16:29:10
layout: post
slug: installing-sap-netweaver-developer-studio
title: Installing SAP Netweaver Developer studio
wordpress_id: 20
categories:
- SAP Enterprise Portal
---

Before installing the studio you must first install the Java SDK:

j2sdk-1_4_2_06-windows-i586-p.exe

Just accept the defaults.

Now install Netweaver Depeloper studio (SP13 in my case)

NWDS_SP13\J2EE-RUNT-CD\IDE\JDTsetup.exe

Install all components.

You will be asked for the location of the Java SDK which if you accepted the default should be:

C:\j2sdk1.4.2_06

Next enter your proxy settings, wwwcache:8080 in my case.

Now sit back, relax and wait for the long install to finish!
