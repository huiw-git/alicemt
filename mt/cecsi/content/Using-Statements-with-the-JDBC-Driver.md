---
title: Using Statements with the JDBC Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
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
# Using Statements with the JDBC Driver
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] can be used to work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database in a variety of ways. The JDBC driver can be used to run SQL statements against the database, or it can be used to call stored procedures in the database, using both input and output parameters. The JDBC driver also supports using SQL escape sequences, update counts, automatically generated keys, and performing updates within a batch operation.  
  
 The JDBC driver provides three classes for retrieving data from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database:  
  
1.  [SQLServerStatement](../content/SQLServerStatement-Class.md) \- used for running SQL statements without parameters.  
  
2.  [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) \- \(inherited from SQLServerStatement\), used for running compiled SQL statements that might contain IN parameters.  
  
3.  [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) \- \(inherited from SQLServerPreparedStatement\), used for running stored procedures that might contain IN parameters, OUT parameters, or both.  
  
 The topics in this section discuss how you can use each of the three statement classes to work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Using Statements with SQL](../content/Using-Statements-with-SQL.md)|Describes how to use SQL statements with the JDBC driver to work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Using Statements with Stored Procedures](../content/Using-Statements-with-Stored-Procedures.md)|Describes how to use stored procedures with the JDBC driver to work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[Using Multiple Result Sets](../content/Using-Multiple-Result-Sets.md)|Describes how to use the JDBC driver to retrieve data from multiple result sets.|  
|[Using SQL Escape Sequences](../content/Using-SQL-Escape-Sequences.md)|Describes how to use SQL escape sequences, such as date and time literals and functions.|  
|[Using Auto Generated Keys](../content/Using-Auto-Generated-Keys.md)|Describes how to use automatically generated keys.|  
|[Performing Batch Operations](../content/Performing-Batch-Operations.md)|Describes how to use the JDBC driver to perform batch operations.|  
|[Handling Complex Statements](../content/Handling-Complex-Statements.md)|Describes how to use the JDBC driver to run complex statements that perform a variety of tasks and might return different types of data.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  