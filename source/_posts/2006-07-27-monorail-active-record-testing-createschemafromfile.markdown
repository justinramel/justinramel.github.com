---
comments: true
date: 2006-07-27 09:21:34
layout: post
slug: monorail-active-record-testing-createschemafromfile
title: Castle Monorail + Active Record + Testing + CreateSchemaFromFile
wordpress_id: 103
categories:
- MonoRail
---

It’s always a good idea to have your test database match your production database exactly, we can do that easily using:

`ActiveRecordStarter.CreateSchemaFromFile()`

Unlike CreateSchema which makes a best guess at how your schema should be CreateSchemaFromFile takes an SQL script which allows you to fully control the database schema.

Call CreateSchemaFromFile as part of your PrepareSchema method in your AbstractTestCase class.

`protected virtual void PrepareSchema()
{
ActiveRecordStarter.DropSchema();
ActiveRecordStarter.CreateSchemaFromFile("schema.sql");
}`

Your schema.sql file should contain scripts in the standard MS SQL format:

`if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[Application_Status]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)
drop table [dbo].[Application_Status]
GO``
CREATE TABLE [dbo].[Application_Status] (
	[ID] [int] NOT NULL ,
	[Title] [varchar] (50) NOT NULL ,
	[Description] [text] NULL
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
`
