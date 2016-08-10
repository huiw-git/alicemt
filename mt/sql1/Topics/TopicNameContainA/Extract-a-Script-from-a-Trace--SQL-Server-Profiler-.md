---
title: "Extract a Script from a Trace (SQL Server Profiler)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Extract a Script from a Trace (SQL Server Profiler)
This topic describes how to extract [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] events from a trace file or table and save them as a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script file by using [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)].  
  
### To extract a Transact-SQL script from a trace file or table  
  
1.  Open a trace file or table that contains [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] events that you want to save to a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script file. For more information, see [Open a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Open-a-Trace-File--SQL-Server-Profiler-.md) or [Open a Trace Table (SQL Server Profiler)](../../Topics/TopicNameContainA/Open-a-Trace-Table--SQL-Server-Profiler-.md).  
  
2.  On the **File** menu, point to **Export**, point to **Extract SQL Server Events**, and then click **Extract Transact-SQL Events**.  
  
3.  In the **Save As** dialog box, type a name for the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] file, and click **Save**.  
  
## See Also  
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md)