---
title: Using an SQL Statement to Modify Data
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
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
# Using an SQL Statement to Modify Data
  To modify the data that is contained in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using an SQL statement, you can use the [executeUpdate](../content/executeUpdate-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class. The executeUpdate method will pass the SQL statement to the database for processing, and then return a value that indicates the number of rows that were affected.  
  
 To do this, you must first create a SQLServerStatement object by using the [createStatement](../content/createStatement-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, an SQL statement is constructed that adds new data to the table, and then the statement is run and the return value is displayed.  
  
 [!CODE [JDBC#UsingSQLToModifyData1](../CodeSnippet/SQLDrivers/jdbc#usingsqltomodifydata1)]  
  
> [!NOTE]  
>  If you must use an SQL statement that contains parameters to modify the data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, you should use the [executeUpdate](../content/executeUpdate-Method--SQLServerPreparedStatement-.md) method of the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class.  
>   
>  If the column that you are trying to insert data into contains special characters such as spaces, you must provide the values to be inserted, even if they are default values. If you do not, the insert operation will fail.  
>   
>  If you want the JDBC driver to return all update counts, including update counts returned by any triggers that may have fired, set the lastUpdateCount connection string property to "false". For more information about the lastUpdateCount property, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
## See Also  
 [Using Statements with SQL](../content/Using-Statements-with-SQL.md)  
  
  