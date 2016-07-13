---
title: Handling Metadata with the JDBC Driver
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
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
# Handling Metadata with the JDBC Driver
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] can be used to work with metadata in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database in a variety of ways. The JDBC driver can be used to get metadata about the database, a result set, or parameters.  
  
 The JDBC driver provides three classes for retrieving metadata from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database:  
  
-   [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md), which is used to return information about the database that is currently connected.  
  
-   [SQLServerResultSetMetaData](../content/SQLServerResultSetMetaData-Class.md), which is used to return information about the result set.  
  
-   [SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md), which is used to return information about the parameters of prepared and callable statements.  
  
 The topics in this section describe how you can use each of the three metadata classes to work with metadata in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
> [!NOTE]  
>  The metadata methods discussed in this section are generally expensive in terms of application performance, so care should be taken with their usage.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Using Database Metadata](../content/Using-Database-Metadata.md)|Describes how to retrieve metadata information about the currently connected database.|  
|[Using Result Set Metadata](../content/Using-Result-Set-Metadata.md)|Describes how to retrieve metadata information about the current result set.|  
|[Using Parameter Metadata](../content/Using-Parameter-Metadata.md)|Describes how to retrieve metadata information about the parameters of prepared and callable statements.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  