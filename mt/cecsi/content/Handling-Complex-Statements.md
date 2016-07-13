---
title: Handling Complex Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
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
# Handling Complex Statements
  When you use the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you might have to handle complex statements, including statements that are dynamically generated at runtime. Complex statements often perform a variety of tasks, including updates, inserts, and deletes. These types of statements might also return multiple result sets and output parameters. In these situations, the Java code that runs the statements might not know in advance the types and number of objects and data returned.  
  
 To effectively process complex statements, the JDBC driver provides a number of methods to query the objects and data that is returned so your application can correctly process them. The key to processing complex statements is the [execute](../content/execute-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class. This method returns a **boolean** value. When the value is true, the first result returned from the statements is a result set. When the value is false, the first result returned was an update count.  
  
 When you know the type of object or data that was returned, you can use either the [getResultSet](../content/getResultSet-Method--SQLServerStatement-.md) or the [getUpdateCount](../content/getUpdateCount-Method--SQLServerStatement-.md) method to process that data. To proceed to the next object or data that is returned from the complex statement, you can call the [getMoreResults](../content/getMoreResults-Method---.md) method.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, a complex statement is constructed that combines a stored procedure call with a SQL statement, the statements are run, and then a `do` loop is used to process all the result sets and updated counts that are returned.  
  
 [!CODE [JDBC#HandlingComplexStatements1](../CodeSnippet/SQLDrivers/jdbc#handlingcomplexstatements1)]  
  
## See Also  
 [Using Statements with the JDBC Driver](../content/Using-Statements-with-the-JDBC-Driver.md)  
  
  