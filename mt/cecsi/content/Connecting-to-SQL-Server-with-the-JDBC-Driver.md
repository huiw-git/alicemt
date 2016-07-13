---
title: Connecting to SQL Server with the JDBC Driver
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
manager: jhubbard
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
# Connecting to SQL Server with the JDBC Driver
  One of the most fundamental things that you will do with the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] is to make a connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. All interaction with the database occurs through the [SQLServerConnection](../content/SQLServerConnection-Class.md) object, and because the JDBC driver has such a flat architecture, almost all interesting behavior touches the SQLServerConnection object.  
  
 If a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] is only listening on an IPv6 port, set the java.net.preferIPv6Addresses system property to make sure that IPv6 is used instead of IPv4 to connect to the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]:  
  
```  
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 The topics in this section describe how to make and work with a connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Building the Connection URL](../content/Building-the-Connection-URL.md)|Describes how to form a connection URL for connecting to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. Also describes connecting to named instances of a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)|Describes the various connection properties and how they can be used when you connect to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Setting the Data Source Properties](../content/Setting-the-Data-Source-Properties.md)|Describes how to use data sources in a Java Platform, Enterprise Edition \(Java EE\) environment.|  
|[Working with a Connection](../content/Working-with-a-Connection.md)|Describes the various ways in which to create an instance of a connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Using Connection Pooling](../content/Using-Connection-Pooling.md)|Describes how the JDBC driver supports the use of connection pooling.|  
|[Using Database Mirroring &#40;JDBC&#41;](../content/Using-Database-Mirroring--JDBC-.md)|Describes how the JDBC driver supports the use of database mirroring.|  
|[JDBC Driver Support for High Availability, Disaster Recovery](../content/JDBC-Driver-Support-for-High-Availability--Disaster-Recovery.md)|Describes how to develop an application that will connect to an AlwaysOn  availability group.|  
|[Using Kerberos Integrated Authentication to Connect to SQL Server](../content/Using-Kerberos-Integrated-Authentication-to-Connect-to-SQL-Server.md)|Discusses a Java implementation for applications to connect to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database using Kerberos integrated authentication.|  
|[Connecting to an Azure SQL database](../content/Connecting-to-an-Azure-SQL-database.md)|Discusses connectivity issues for databases on SQL Azure.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  