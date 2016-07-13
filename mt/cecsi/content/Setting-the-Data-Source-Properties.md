---
title: Setting the Data Source Properties
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
manager:jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# Setting the Data Source Properties
  Data sources are the preferred mechanism by which to create JDBC connections in a Java Platform, Enterprise Edition \(Java EE\) environment. Data sources provide connections, pooled connections, and distributed connections without hard\-coding connection properties into Java code. All [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] data sources can set or get the value of any property by using the appropriate setter and getter methods, respectively.  
  
 Java EE products, such as application servers and servlet\/JSP engines, typically let you configure data sources for database access. Any property listed in the [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md) topic can be specified wherever the configuration lets you enter a property as a property\=value pair.  
  
 For more information about [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data sources, see the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class. For an example of how to use the SQLServerDataSource class to make a connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, see [Data Source Sample](../content/Data-Source-Sample.md).  
  
## See Also  
 [Connecting to SQL Server with the JDBC Driver](../content/Connecting-to-SQL-Server-with-the-JDBC-Driver.md)  
  
  