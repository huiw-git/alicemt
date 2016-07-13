---
title: Working with Data Types (JDBC)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
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
# Working with Data Types (JDBC)
  The primary function of the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] is to allow Java developers to access data contained in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] databases. To accomplish this, the JDBC driver mediates the conversion between [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types and Java language types and objects.  
  
> [!NOTE]  
>  For a detailed discussion of the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and JDBC driver data types, including their differences and how they are converted to Java language data types, see [Understanding the JDBC Driver Data Types](../content/Understanding-the-JDBC-Driver-Data-Types.md).  
  
 In order to work with SQL Server data types, the JDBC driver provides get\<Type\> and set\<Type\> methods for the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) and [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) classes, and it provides get\<Type\> and update\<Type\> methods for the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class. Which method you use depends on the type of data that you are working with, and whether you are using result sets or queries.  
  
 The topics in this section describe how to use the JDBC driver data types to access [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data in your Java applications.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Basic Data Types Sample](../content/Basic-Data-Types-Sample.md)|Describes how to use result set getter methods to retrieve basic [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type values, and how to use result set update methods to update those values.|  
|[SQLXML Data Type Sample](../content/SQLXML-Data-Type-Sample.md)|Describes how to store an XML data in a relational database, how to retrieve an XML data from a database, and how to parse an XML data with the **SQLXML** Java data type.|  
  
## See Also  
 [Sample JDBC Driver Applications](../content/Sample-JDBC-Driver-Applications.md)  
  
  