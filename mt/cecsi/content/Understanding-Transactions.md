---
title: Understanding Transactions
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
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
# Understanding Transactions
  Transactions are groups of operations that are combined into logical units of work. They are used to control and maintain the consistency and integrity of each action in a transaction, despite errors that might occur in the system.  
  
 With the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], transactions can be either local or distributed. Transactions can also use isolation levels. For more information about the isolation levels supported by the JDBC driver, see [Understanding Isolation Levels](../content/Understanding-Isolation-Levels.md).  
  
 Applications should control transactions by either using Transact\-SQL statements or the methods provided by the JDBC driver, but not both. Using both Transact\-SQL statements and JDBC API methods on the same transaction might lead to problems, such as a transaction cannot be committed when expected, a transaction is committed or rolled back and a new one starts unexpectedly, or "Failed to resume the transaction" exceptions.  
  
## Using Local Transactions  
 A transaction is considered to be local when it is a single\-phase transaction, and it is handled by the database directly. The JDBC driver supports local transactions by using various methods of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class, including [setAutoCommit](../content/setAutoCommit-Method--SQLServerConnection-.md), [commit](../content/commit-Method--SQLServerConnection-.md), and [rollback](../content/rollback-Method---.md). Local transactions are typically managed explicitly by the application or automatically by the Java Platform, Enterprise Edition \(Java EE\) application server.  
  
 The following example performs a local transaction that consists of two separate statements in the `try` block. The statements are run against the Production.ScrapReason table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database, and they are committed if no exceptions are thrown. The code in the `catch` block rolls back the transaction if an exception is thrown.  
  
 [!CODE [JDBC#UnderstandingTransactions1](../CodeSnippet/SQLDrivers/jdbc#understandingtransactions1)]  
  
## Using Distributed Transactions  
 A distributed transaction updates data on two or more networked databases while retaining the important atomic, consistent, isolated, and durable \(ACID\) properties of transaction processing. Distributed transaction support was added to the JDBC API in the JDBC 2.0 Optional API specification. The management of distributed transactions is typically performed automatically by the Java Transaction Service \(JTS\) transaction manager in a Java EE application server environment. However, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports distributed transactions under any Java Transaction API \(JTA\) compliant transaction manager.  
  
 The JDBC driver seamlessly integrates with [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Distributed Transaction Coordinator \(MS DTC\) to provide true distributed transaction support with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. MS DTC is a distributed transaction facility provided by [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] for [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows systems. MS DTC uses proven transaction processing technology from [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] to support XA features such as the complete two\-phase distributed commit protocol and the recovery of distributed transactions.  
  
 For more information about how to use distributed transactions, see [Understanding XA Transactions](../content/Understanding-XA-Transactions.md).  
  
## See Also  
 [Performing Transactions with the JDBC Driver](../content/Performing-Transactions-with-the-JDBC-Driver.md)  
  
  