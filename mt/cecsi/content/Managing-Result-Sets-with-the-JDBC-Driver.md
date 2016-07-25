---
title: "Managing Result Sets with the JDBC Driver"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
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
# Managing Result Sets with the JDBC Driver
  The result set is an object that represents a set of data returned from a data source, usually as the result of a query. The result set contains rows and columns to hold the requested data elements, and it is navigated with a cursor. A result set can be updatable, meaning that it can be modified and have those modifications pushed to the original data source. A result set can also have various levels of sensitivity to changes in the underlying data source.  
  
 The type of result set is determined when a statement is created, which is when a call to the [createStatement](../content/createStatement-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class is made. The fundamental role of a result set is to provide Java applications with a usable representation of the database data. This is typically done with the typed getter and setter methods on the result set data elements.  
  
 In the following example, which is based on the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database, a result set is created by calling the [executeQuery](../content/executeQuery-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class. Data from the result set is then displayed by using the [getString](../content/getString-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
 [!CODE [JDBC#ManagingResultSets1](../CodeSnippet/SQLDrivers/jdbc#managingresultsets1)]  
  
 The topics in this section describe various aspects of result set usage, including cursor types, concurrency, and row locking.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Understanding Cursor Types](../content/Understanding-Cursor-Types.md)|Describes the different cursor types that the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports.|  
|[Understanding Concurrency Control](../content/Understanding-Concurrency-Control.md)|Describes how the JDBC driver supports concurrency control.|  
|[Understanding Row Locking](../content/Understanding-Row-Locking.md)|Describes how the JDBC driver supports row locking.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  