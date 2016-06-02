---
title: Cross-Database Queries
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
---
# Cross-Database Queries
  In [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)], memory\-optimized tables do not support cross\-database transactions. You cannot access another database from the same transaction or the same query that also accesses a memory\-optimized table. You cannot easily copy data from a table in one database, to a memory\-optimized table in another database.  
  
 Table variables are not transactional. Therefore, memory\-optimized table variables can be used in cross\-database queries, and can thus facilitate moving data from one database into memory\-optimized tables in another. You can use two transactions. In the first transaction, insert the data from the remote table into the variable. In the second transaction, insert the data into the local memory\-optimized table from the variable.  
  
 For example, to copy the row from table t1 in database db1 to table t2 in db2, using variable @v1 of type dbo.tt1, you can use something like:  
  
```tsql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## See Also  
 [Migrating to In-Memory OLTP](../../Topics\TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)  
  
  