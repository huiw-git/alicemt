---
title: Using Database Metadata
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
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
# Using Database Metadata
  To query a database for information about what it supports, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] implements the [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) class. This class contains numerous methods that return information in the form of a single value, or as a result set.  
  
 To create a SQLServerDatabaseMetaData object, you can use the [getMetaData](../content/getMetaData-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class to get information about the database that it is connected to.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, the getMetaData method of the SQLServerConnection class is used to return a SQLServerDatabaseMetadata object, and then various methods of the SQLServerDatabaseMetaData object are used to display information about the driver, driver version, database name, and database version.  
  
 [!CODE [JDBC#UsingDBMetaData1](../CodeSnippet/SQLDrivers/jdbc#usingdbmetadata1)]  
  
## See Also  
 [Handling Metadata with the JDBC Driver](../content/Handling-Metadata-with-the-JDBC-Driver.md)  
  
  