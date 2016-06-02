---
title: SQL Server Profiler Templates and Permissions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
---
# SQL Server Profiler Templates and Permissions
  [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] shows how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resolves queries internally. This allows administrators to see exactly what [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements or Multi\-Dimensional Expressions are submitted to the server and how the server accesses the database or cube to return result sets.  
  
 Using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], you can do the following:  
  
-   Create a trace that is based on a reusable template  
  
-   Watch the trace results as the trace runs  
  
-   Store the trace results in a table  
  
-   Start, stop, pause, and modify the trace results as necessary  
  
-   Replay the trace results  
  
 Use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to monitor only the events in which you are interested. If traces are becoming too large, you can filter them based on the information you want, so that only a subset of the event data is collected. Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.  
  
> [!NOTE]  
>  Trace column values greater than 1 GB return an error and are truncated in the trace output.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[SQL Server Profiler Templates](../../Topics\TopicNameNotContainA/SQL-Server-Profiler-Templates.md)|Contains information about the predefined trace templates that ship with [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].|  
|[Permissions Required to Run SQL Server Profiler](../../Topics\TopicNameNotContainA/Permissions-Required-to-Run-SQL-Server-Profiler.md)|Contains information about the permissions that are required to run [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].|  
|[Save Traces and Trace Templates](../../Topics\TopicNameNotContainA/Save-Traces-and-Trace-Templates.md)|Contains information about saving trace output and about saving trace definitions into a template.|  
|[Modify Trace Templates](../../Topics\TopicNameNotContainA/Modify-Trace-Templates.md)|Contains information about modifying trace templates by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] or by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].|  
|[Start a Trace](../../Topics\TopicNameContainA/Start-a-Trace.md)|Contains information about what happens when you start, pause, or stop a trace.|  
|[Correlate a Trace with Windows Performance Log Data](../../Topics\TopicNameContainA/Correlate-a-Trace-with-Windows-Performance-Log-Data.md)|Contains information about correlating Windows performance log data with a trace by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Profiler.|  
|[View and Analyze Traces with SQL Server Profiler](../../Topics\TopicNameNotContainA/View-and-Analyze-Traces-with-SQL-Server-Profiler.md)|Contains information about using traces to troubleshoot data, displaying object names in a trace, and finding events in a trace.|  
|[Analyze Deadlocks with SQL Server Profiler](../../Topics\TopicNameNotContainA/Analyze-Deadlocks-with-SQL-Server-Profiler.md)|Contains information about using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to identify the cause of a deadlock.|  
|[Analyze Queries with SHOWPLAN Results in SQL Server Profiler](../../Topics\TopicNameNotContainA/Analyze-Queries-with-SHOWPLAN-Results-in-SQL-Server-Profiler.md)|Contains information about using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to collect and display Showplan and Showplan Statistics results.|  
|[Filter Traces with SQL Server Profiler](../../Topics\TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md)|Contains information about setting filters on data columns to filter trace output by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].|  
|[Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)|Contains information that explains what replaying a trace means and what is required to replay a trace.|  
  
## See Also  
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)   
 [Start SQL Server Profiler](../../Topics\TopicNameNotContainA/Start-SQL-Server-Profiler.md)  
  
  