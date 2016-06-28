---
title: Connecting and Retrieving Data
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
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
# Connecting and Retrieving Data
  When you are working with the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], there are two primary methods for establishing a connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database. One is to set connection properties in the connection URL, and then call the getConnection method of the DriverManager class to return a [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
> [!NOTE]  
>  For a list of the connection properties supported by the JDBC driver, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 The second method involves setting the connection properties by using setter methods of the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class, and then calling the [getConnection](../content/getConnection-Method--SQLServerDataSource-.md) method to return a SQLServerConnection object.  
  
 The topics in this section describe the different ways in which you can connect to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, and they also demonstrate different techniques for retrieving data.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Connection URL Sample](../content/Connection-URL-Sample.md)|Describes how to use a connection URL to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and then use an SQL statement to retrieve data.|  
|[Data Source Sample](../content/Data-Source-Sample.md)|Describes how to use a data source to connect to SQL Server and then use a stored procedure to retrieve data.|  
  
## See Also  
 [Sample JDBC Driver Applications](../content/Sample-JDBC-Driver-Applications.md)  
  
  