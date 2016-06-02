---
title: Implementing MERGE Functionality in a Natively Compiled Stored Procedure
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
---
# Implementing MERGE Functionality in a Natively Compiled Stored Procedure
  A database may need to perform either an insert of an update, depending on whether a particular row already exists in the database.  
  
 Without using the **MERGE** statement, the following is one approach you can use in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]:  
  
```tsql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Another [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] method to implement a merge:  
  
```tsql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE….  
ELSE  
    INSERT  
```  
  
 For a natively compiled stored procedure  
  
```tsql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT….  
```  
  
## See Also  
 [Migration Issues for Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Migration-Issues-for-Natively-Compiled-Stored-Procedures.md)   
 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Constructs-Not-Supported-by-In-Memory-OLTP.md)  
  
  