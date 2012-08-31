---
comments: true
date: 2009-01-23 16:38:12
layout: post
slug: castle-activerecord-exception-the-proxyfactoryfactory-was-not-configured
title: 'Castle ActiveRecord – Exception : The ProxyFactoryFactory was not configured'
wordpress_id: 141
categories:
- ActiveRecord
- Castle
tags:
- Active Record
- Castle
---

I’ve just updated to the latest version of the Castle stack and got hit with this exception:

 
    
    The ProxyFactoryFactory was not configured.
    Initialize 'proxyfactory.factory_class' property of the session-factory configuration section with one of the available NHibernate.ByteCode providers.
    Example:
    NHibernate.ByteCode.LinFu.ProxyFactoryFactory, NHibernate.ByteCode.LinFu
    Example:
    NHibernate.ByteCode.Castle.ProxyFactoryFactory, NHibernate.ByteCode.Castle





Turns out the NHibernate config has changed and as the exception says you must now specify a factory class.





To fix the exception add a new line to your active record facility config:





<facility id="activerecord.facility" isweb="true" type="Castle.Facilities.ActiveRecordIntegration.ActiveRecordFacility, Castle.Facilities.ActiveRecordIntegration">
    
<assemblies>

    
<item>Nu.Core</item>

    
</assemblies>

    
<config>

    
<add value="false" key="cache.use_query_cache" />

    
<add value="ReadCommitted" key="connection.isolation" />

    
<add value="false" key="show_sql" />

    
<add value="NHibernate.Dialect.SQLiteDialect" key="dialect" />

    
<add value="NHibernate.Driver.SQLite20Driver" key="connection.driver_class" />

    
<add value="true=1;false=0" key="query.substitutions" />

    
<add value="#{ConnectionString}" key="connection.connection_string" />

    
<add value="NHibernate.Connection.DriverConnectionProvider" key="connection.provider" />

    
** <add value="NHibernate.ByteCode.Castle.ProxyFactoryFactory, NHibernate.ByteCode.Castle" key="proxyfactory.factory_class" />
      
** </config>

    
</facility>





Then add a reference in your project to NHibernate.ByteCode.Castle.dll.
