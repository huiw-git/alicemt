---
title: "Using an SQL Statement to Modify Database Objects"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
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
# Using an SQL Statement to Modify Database Objects
  To modify [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database objects by using an SQL statement, you can use the [executeUpdate](../content/executeUpdate-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class. The executeUpdate method will pass the SQL statement to the database for processing, and then return a value of 0 because no rows were affected.  
  
 To do this, you must first create a SQLServerStatement object by using the [createStatement](../content/createStatement-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class.  
  
> [!NOTE]  
>  SQL statements that modify objects within a database are called Data Definition Language (DDL) statements. These include statements such as CREATE TABLE, DROP TABLE, CREATE INDEX, and DROP INDEX. For more information about the types of DDL statements that are supported by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], see [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, an SQL statement is constructed that will create the simple TestTable in the database, and then the statement is run and the return value is displayed.  
  
 [!CODE [JDBC#UsingSQLToModifyDBObjects1](../CodeSnippet/SQLDrivers/jdbc#usingsqltomodifydbobjects1)]  
  
## See Also  
 [Using Statements with SQL](../content/Using-Statements-with-SQL.md)  
  
  