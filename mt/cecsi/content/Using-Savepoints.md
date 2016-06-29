---
title: Using Savepoints
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
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
# Using Savepoints
  Savepoints offer a mechanism to roll back portions of transactions. Within [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], you can create a savepoint by using the SAVE TRANSACTION savepoint\_name statement. Later, you run a ROLLBACK TRANSACTION savepoint\_name statement to roll back to the savepoint instead of rolling back to the start of the transaction.  
  
 Savepoints are useful in situations where errors are unlikely to occur. The use of a savepoint to roll back part of a transaction in the case of an infrequent error can be more efficient than having each transaction test to see if an update is valid before making the update. Updates and rollbacks are expensive operations, so savepoints are effective only if the probability of encountering the error is low and the cost of checking the validity of an update beforehand is relatively high.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports the use of savepoints through the [setSavepoint](../content/setSavepoint-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class. By using the setSavepoint method, you can create a named or unnamed savepoint within the current transaction, and the method will return a [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object. Multiple savepoints can be created within a transaction. To roll back a transaction to a given savepoint, you can pass the SQLServerSavepoint object to the [rollback \(java.sql.Savepoint\)](../content/rollback-Method--java.sql.Savepoint-.md) method.  
  
 In the following example, a savepoint is used while performing a local transaction consisting of two separate statements in the `try` block. The statements are run against the Production.ScrapReason table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database, and a savepoint is used to roll back the second statement. This results in only the first statement being committed to the database.  
  
 [!CODE [JDBC#UsingSavepoints1](../CodeSnippet/SQLDrivers/jdbc#usingsavepoints1)]  
  
## See Also  
 [Performing Transactions with the JDBC Driver](../content/Performing-Transactions-with-the-JDBC-Driver.md)  
  
  