---
title: Using an SQL Statement with Parameters
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
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
# Using an SQL Statement with Parameters
  To work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using an SQL statement that contains IN parameters, you can use the [executeQuery](../content/executeQuery-Method--SQLServerPreparedStatement-.md) method of the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class to return a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) that will contain the requested data. To do this, you must first create a SQLServerPreparedStatement object by using the [prepareStatement](../content/prepareStatement-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class.  
  
 When you construct your SQL statement, the IN parameters are specified by using the ? \(question mark\) character, which acts as a placeholder for the parameter values that will later be passed into the SQL statement. To specify a value for a parameter, you can use one of the setter methods of the SQLServerPreparedStatement class. The setter method that you use is determined by the data type of the value that you want to pass into the SQL statement.  
  
 When you pass a value to the setter method, you must specify not only the actual value to be used in the SQL statement, but also the parameter's ordinal placement in the SQL statement. For example, if your SQL statement contains a single parameter, its ordinal value will be 1. If the statement contains two parameters, the first ordinal value will be 1, while the second ordinal value will be 2.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, an SQL prepared statement is constructed and run with a single String parameter value, and then the results are read from the result set.  
  
 [!CODE [JDBC#UsingSQLWithParams1](../CodeSnippet/SQLDrivers/jdbc#usingsqlwithparams1)]  
  
## See Also  
 [Using Statements with SQL](../content/Using-Statements-with-SQL.md)  
  
  