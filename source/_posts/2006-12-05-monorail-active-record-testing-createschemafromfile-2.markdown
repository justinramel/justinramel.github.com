---
comments: true
date: 2006-12-05 12:24:11
layout: post
slug: monorail-active-record-testing-createschemafromfile-2
title: Castle Monorail + Active Record + Testing + CreateSchemaFromFile
wordpress_id: 102
categories:
- MonoRail
---

It’s always a good idea to have your test database match your production database exactly to do that use:

`ActiveRecordStarter.CreateSchemaFromFile()`

Unlike CreateSchema which takes a best guess at how your schema should be CreateSchemaFromFile uses an SQL script which allows you to control exactly what the schema should be.

Call CreateSchemaFromFile as part of your PrepareSchema method in your AbstractTestCase class.

`protected virtual void PrepareSchema()
{
// If you want to delete everything from the model.
// Remember to do it in a descendent dependency order
// Office.DeleteAll();
// User.DeleteAll();
// Another approach is to always recreate the schema
// (please use a separate test database if you want to do that)
ActiveRecordStarter.DropSchema();
ActiveRecordStarter.CreateSchemaFromFile("schema.sql");
}`

Your schema.sql file should contain scripts in the standard MS SQL format:

`if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[Application_Status]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)
drop table [dbo].[Application_Status]
GO

CREATE TABLE [dbo].[Application_Status] (
	[ID] [int] NOT NULL ,
	[Title] [varchar] (50) NOT NULL ,
	[Description] [text] NULL
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
`
