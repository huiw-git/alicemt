---
title: Using Holdability
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
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
# Using Holdability
  By default, a result set created within a transaction is kept open after the transaction is committed to the database, or when it is rolled back. However, it is sometimes useful for the result set to be closed, after the transaction has been committed. To do this, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports the use of result set holdability.  
  
 Result set holdability can be set by using the [setHoldability](../content/setHoldability-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class. When setting the holdability by using the setHoldability method, the result set holdability constants of ResultSet.HOLD\_CURSORS\_OVER\_COMMIT or ResultSet.CLOSE\_CURSORS\_AT\_COMMIT can be used.  
  
 The JDBC driver also supports setting holdability when creating one of the Statement objects. When creating the Statement objects that have overloads with result set holdability parameters, the holdability of statement object must match the connection's holdability. When they don't match, an exception is thrown. This is because SQL Server supports the holdability only at the connection level.  
  
 The holdability of a result set is the holdability of the SQLServerConnection object that is associated with the result set at the time when the result set is created for server\-side cursors only. It does not apply to client\-side cursors. All result sets with client\-side cursors will always have the holdability value of ResultSet.HOLD\_CURSORS\_OVER\_COMMIT.  
  
 For server cursors, when connected to SQL Server 2005 or later, setting the holdability affects only the holdability of new result sets that are yet to be created on that connection. This means that setting holdability has no impact on the holdability of any result sets that were previously created and are already open on that connection. However, with SQL Server 2000, setting holdability affects the holdability of both existing result sets and new result sets that are yet to be created on that connection.  
  
 In the following example, the result set holdability is set while performing a local transaction consisting of two separate statements in the `try` block. The statements are run against the Production.ScrapReason table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. First, the example switches to manual transaction mode by setting the auto\-commit to **false**. Once auto\-commit mode is disabled, no SQL Statements will be committed until the application calls the [commit](../content/commit-Method--SQLServerConnection-.md) method explicitly. The code in the catch block rolls back the transaction if an exception is thrown.  
  
 [!CODE [JDBC#UsingHoldability1](../CodeSnippet/SQLDrivers/jdbc#usingholdability1)]  
  
## See Also  
 [Performing Transactions with the JDBC Driver](../content/Performing-Transactions-with-the-JDBC-Driver.md)  
  
  