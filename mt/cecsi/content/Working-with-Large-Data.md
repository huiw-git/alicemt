---
title: "Working with Large Data"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
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
# Working with Large Data
  The JDBC driver provides support for adaptive buffering, which allows you to retrieve any kind of large-value data without the overhead of server cursors. With adaptive buffering, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] retrieves statement execution results from the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] as the application needs them, rather than all at once. The driver also discards the results as soon as the application can no longer access them.  
  
 In the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] JDBC Driver version 1.2, the buffering mode was "**full**" by default. If your application did not set the "responseBuffering" connection property to "**adaptive**" either in the connection properties or by using the [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) object, the driver supported reading the entire result from the server at once. In order to get the adaptive buffering behavior, your application had to set the "responseBuffering" connection property to "**adaptive**" explicitly.  
  
 The **adaptive** value is the default buffering mode and the JDBC driver buffers the minimum possible data when necessary. For more information about using adaptive buffering, see [Using Adaptive Buffering](../content/Using-Adaptive-Buffering.md).  
  
 The topics in this section describe different ways that you can use to retrieve large-value data from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Reading Large Data Sample](../content/Reading-Large-Data-Sample.md)|Describes how to use a SQL statement to retrieve large-value data.|  
|[Reading Large Data with Stored Procedures Sample](../content/Reading-Large-Data-with-Stored-Procedures-Sample.md)|Describes how to retrieve a large CallableStatement OUT parameter value.|  
|[Updating Large Data Sample](../content/Updating-Large-Data-Sample.md)|Describes how to update a large-value data in a database.|  
  
## See Also  
 [Sample JDBC Driver Applications](../content/Sample-JDBC-Driver-Applications.md)  
  
  