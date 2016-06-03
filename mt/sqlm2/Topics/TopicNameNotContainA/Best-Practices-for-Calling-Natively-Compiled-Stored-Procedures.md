---
title: Best Practices for Calling Natively Compiled Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
---
# Best Practices for Calling Natively Compiled Stored Procedures
  Natively compiled stored procedures are:  
  
-   Used typically in performance\-critical parts of an application.  
  
-   Frequently executed.  
  
-   Expected to be very fast.  
  
 The performance benefit of using a natively compiled stored procedure increases with the number of rows and the amount of logic that is processed by the procedure. For example, a natively compiled stored procedure will exhibit better performance if it uses one or more of the following:  
  
-   Aggregation.  
  
-   Nested\-loops joins.  
  
-   Multi\-statement select, insert, update, and delete operations.  
  
-   Complex expressions.  
  
-   Procedural logic, such as conditional statements and loops.  
  
 If you need to process only a single row, using a natively compiled stored procedure may not provide a performance benefit.  
  
 To avoid the server having to map parameter names and convert types:  
  
-   Match the types of the parameters passed to the procedure with the types in the procedure definition.  
  
-   Use ordinal \(nameless\) parameters when calling natively compiled stored procedures. For the most efficient execution, do not use named parameters.  
  
 Use of \(inefficient\) named parameters with natively compiled stored procedures can be detected through the XEvent **hekaton\_slow\_parameter\_passing**, with **reason\=named\_parameters**.  
  
 Similarly, you can detect use of mismatched types through the same XEvent **hekaton\_slow\_parameter\_passing**, with **reason\=parameter\_conversion**.  
  
 Because you will need to implement retry logic when using memory\-optimized tables \(in many scenarios\), and because you will need to work around certain feature limitations, you may want to create a wrapper interpreted [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stored procedure. For an example, see [Transactions with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Transactions-with-Memory-Optimized-Tables.md).  
  
## See Also  
 [Natively Compiled Stored Procedures](../../Topics\TopicNameNotContainA/Natively-Compiled-Stored-Procedures.md)  
  
  