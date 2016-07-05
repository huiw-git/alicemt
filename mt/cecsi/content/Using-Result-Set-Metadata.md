---
title: Using Result Set Metadata
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
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
# Using Result Set Metadata
  To query a result set for information about the columns that it contains, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] implements the [SQLServerResultSetMetaData](../content/SQLServerResultSetMetaData-Class.md) class. This class contains numerous methods that return information in the form of a single value.  
  
 To create a SQLServerResultSetMetaData object, you can use the [getMetaData](../content/getMetaData-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, the getMetaData method of the SQLServerResultSet class is used to return a SQLServerResultSetMetaData object, and then various methods of the SQLServerResultSetMetaData object are used to display information about the name and data type of the columns contained within the result set.  
  
 [!CODE [JDBC#UsingResultSetMetaData1](../CodeSnippet/SQLDrivers/jdbc#usingresultsetmetadata1)]  
  
## See Also  
 [Handling Metadata with the JDBC Driver](../content/Handling-Metadata-with-the-JDBC-Driver.md)  
  
  