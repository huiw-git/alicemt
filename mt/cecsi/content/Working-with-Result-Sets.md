---
title: Working with Result Sets
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
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
# Working with Result Sets
  When you work with the data contained in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, one method of manipulating the data is to use a result set. The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports the use of result sets through the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object. By using the SQLServerResultSet object, you can retrieve the data returned from an SQL statement or stored procedure, update the data as needed, and then persist that data back to the database.  
  
 In addition, the SQLServerResultSet object provides methods for navigating through its rows of data, getting or setting the data that it contains, and for establishing various levels of sensitivity to changes in the underlying database.  
  
> [!NOTE]  
>  For more information about managing result sets, including their sensitivity to changes, see [Managing Result Sets with the JDBC Driver](../content/Managing-Result-Sets-with-the-JDBC-Driver.md).  
  
 The topics in this section describe different ways that you can use a result set to manipulate the data contained in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Retrieving Result Set Data Sample](../content/Retrieving-Result-Set-Data-Sample.md)|Describes how to use a result set to retrieve data from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database and display it.|  
|[Modifying Result Set Data Sample](../content/Modifying-Result-Set-Data-Sample.md)|Describes how to use a result set to insert, retrieve, and modify data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Caching Result Set Data Sample](../content/Caching-Result-Set-Data-Sample.md)|Describes how to use a result set to retrieve large amounts of data from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, and to control how that data is cached on the client.|  
  
## See Also  
 [Sample JDBC Driver Applications](../content/Sample-JDBC-Driver-Applications.md)  
  
  