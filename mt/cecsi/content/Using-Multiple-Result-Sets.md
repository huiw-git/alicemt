---
title: "Using Multiple Result Sets"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
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
# Using Multiple Result Sets
  When working with inline SQL or [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedures that return more than one result set, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the [getResultSet](../content/getResultSet-Method--SQLServerStatement-.md) method in the [SQLServerStatement](../content/SQLServerStatement-Class.md) class for retrieving each set of data returned. In addition, when running a statement that returns more than one result set, you can use the [execute](../content/execute-Method--SQLServerStatement-.md) method of the SQLServerStatement class, because it will return a **boolean** value that indicates if the value returned is a result set or an update count.  
  
 If the execute method returns **true**, the statement that was run has returned one or more result sets. You can access the first result set by calling the getResultSet method. To determine if more result sets are available, you can call the [getMoreResults](../content/getMoreResults-Method--SQLServerStatement-.md) method, which returns a **boolean** value of **true** if more result sets are available. If more result sets are available, you can call the getResultSet method again to access them, continuing the process until all result sets have been processed. If the getMoreResults method returns **false**, there are no more result sets to process.  
  
 If the execute method returns **false**, the statement that was run has returned an update count value, which you can retrieve by calling the [getUpdateCount](../content/getUpdateCount-Method--SQLServerStatement-.md) method.  
  
> [!NOTE]  
>  For more information about update counts, see [Using a Stored Procedure with an Update Count](../content/Using-a-Stored-Procedure-with-an-Update-Count.md).  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, and an SQL statement is constructed that, when run, returns two result sets:  
  
 [!CODE [JDBC#UsingMultipleResultSets1](../CodeSnippet/SQLDrivers/jdbc#usingmultipleresultsets1)]  
  
 In this case, the number of result sets returned is known to be two. However, the code is written so that if an unknown number of result sets were returned, such as when calling a stored procedure, they would all be processed. To see an example of calling a stored procedure that returns multiple result sets along with update values, see [Handling Complex Statements](../content/Handling-Complex-Statements.md).  
  
> [!NOTE]  
>  When you make the call to the getMoreResults method of the SQLServerStatement class, the previously returned result set is implicitly closed.  
  
## See Also  
 [Using Statements with the JDBC Driver](../content/Using-Statements-with-the-JDBC-Driver.md)  
  
  