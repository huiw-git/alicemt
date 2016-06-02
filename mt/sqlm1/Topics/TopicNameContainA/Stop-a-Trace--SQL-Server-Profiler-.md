---
title: Stop a Trace (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
---
# Stop a Trace (SQL Server Profiler)
  This topic describes how to stop a trace that is running by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
 Stopping a trace stops data from being captured. After a trace is stopped, it cannot be restarted without losing previously captured data, unless the data has been captured to a trace file or trace table. You can also save the collected data to a table or file after stopping a trace. All trace properties that were previously selected are preserved when a trace is stopped. When a trace is stopped, you can change the name, events, columns, and filters.  
  
### To stop a trace  
  
1.  Select a trace that is running.  
  
2.  On the **File** menu, click **Stop Trace**.  
  
## See Also  
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)  
  
  