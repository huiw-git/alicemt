---
title: Using an SQL Statement with No Parameters
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
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
# Using an SQL Statement with No Parameters
  To work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using an SQL statement that contains no parameters, you can use the [executeQuery](../content/executeQuery-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class to return a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) that will contain the requested data. To do this, you must first create a SQLServerStatement object by using the [createStatement](../content/createStatement-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, an SQL statement is constructed and run, and then the results are read from the result set.  
  
 [!CODE [JDBC#UsingSQLWithNoParams1](../CodeSnippet/SQLDrivers/jdbc#usingsqlwithnoparams1)]  
  
 For more information about using result sets, see [Managing Result Sets with the JDBC Driver](../content/Managing-Result-Sets-with-the-JDBC-Driver.md).  
  
## See Also  
 [Using Statements with SQL](../content/Using-Statements-with-SQL.md)  
  
  