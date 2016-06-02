---
title: Simulating an IF-WHILE EXISTS Statement in a Natively Compiled Module
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
---
# Simulating an IF-WHILE EXISTS Statement in a Natively Compiled Module
  Natively compiled stored procedures do not support the **EXISTS** clause in conditional statements such as IF and WHILE.  
  
 The following example illustrates a workaround using a BIT variable with a SELECT statement to simulate an EXISTS clause:  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## See Also  
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)   
 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md)  
  
  