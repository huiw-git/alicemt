---
title: "Implementing IDENTITY in a Memory-Optimized Table"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Implementing IDENTITY in a Memory-Optimized Table
IDENTITY(1, 1) is supported on a memory-optimized table. However, identity columns with definition of IDENTITY(x, y) where x != 1 or y != 1 are not supported on memory-optimized tables. The workaround for IDENTITY values uses the SEQUENCE object ([Sequence Numbers](../../Topics/TopicNameNotContainA/Sequence-Numbers.md)).  
  
 First remove the IDENTITY property from the table you are converting to In-Memory OLTP. Then, define a new SEQUENCE object for the column in the table. SEQUENCE objects as identity columns rely on the ability to create DEFAULT values for columns that use the NEXT VALUE FOR syntax to get a new identity value. Since DEFAULTs are not supported in In-Memory OLTP, you need to pass the newly-generated SEQUENCE value either to the INSERT statement or to a natively compiled stored procedure that does the insert.  
  
 The following Transact-SQL code example demonstrates the pattern.  
  
```tsql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert.  
-- Here the column C1 was the identity column in the original table.  
--  
create table T1  
(  
  [c1] integer not null constraint T1_c1 primary key nonclustered,  
  [c2] varchar(32) not null,  
  [c3] datetime not null  
) with (memory_optimized = on);  
go  
  
-- This is a sequence provider that will give us values for column [c1].  
--  
create SEQUENCE usq_SequenceForT1  
  as integer  
  start with 2   -- 2 would fail for Identity on a memory_optimized table.  
  increment by 1;  
go  
  
--   Insert a sample row using the sequence.  
--   A new value needs to be retrieved from   
--   the sequence object for every insert.  
--  
declare @c1 integer = NEXT VALUE FOR [dbo].[usq_SequenceForT1];  
  
insert into T1 values (@c1, 'test', getdate());  
```  
  
 After performing the insert several times, you see valid monotonically increasing values in column [c1]. This result set is generated using table scan and hash index without **ORDER BY** so the rows are not ordered.  
  
## See Also  
 [Migrating to In-Memory OLTP](../../Topics/TopicNameNotContainA/Migrating-to-In-Memory-OLTP.md)