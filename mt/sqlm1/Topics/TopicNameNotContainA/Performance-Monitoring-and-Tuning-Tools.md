---
title: Performance Monitoring and Tuning Tools
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
---
# Performance Monitoring and Tuning Tools
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a comprehensive set of tools for monitoring events in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and for tuning the physical database design. The choice of tool depends on the type of monitoring or tuning to be done and the particular events to be monitored.  
  
 Following are the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] monitoring and tuning tools:  
  
|Tool|Description|  
|----------|-----------------|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../Topic/sp_trace_setfilter%20\(Transact-SQL\).md)|[!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] tracks engine process events, such as the start of a batch or a transaction, enabling you to monitor server and database activity \(for example, deadlocks, fatal errors, or login activity\). You can capture [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] data to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table or a file for later analysis, and you can also replay the events captured on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] step by step, to see exactly what happened.|  
|[SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md)|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay can use multiple computers to replay trace data, simulating a mission\-critical workload.|  
|[Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)|System Monitor primarily tracks resource usage, such as the number of buffer manager page requests in use, enabling you to monitor server performance and activity using predefined objects and counters or user\-defined counters to monitor events. System Monitor \(Performance Monitor in Microsoft Windows NT 4.0\) collects counts and rates rather than data about the events \(for example, memory usage, number of active transactions, number of blocked locks, or CPU activity\). You can set thresholds on specific counters to generate alerts that notify operators.<br /><br /> System Monitor works on Microsoft Windows Server and Windows operating systems. It can monitor \(remotely or locally\) an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on Windows NT 4.0 or later.<br /><br /> The key difference between [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] and System Monitor is that [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] monitors Database Engine events, whereas System Monitor monitors resource usage associated with server processes.|  
|[Open Activity Monitor &#40;SQL Server Management Studio&#41;](../Topic/Open%20Activity%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)|The Activity Monitor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] is useful for ad hoc views of current activity and graphically displays information about:<br /><br /> Processes running on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].<br /><br /> Blocked processes.<br /><br /> Locks.<br /><br /> User activity.|  
|[Live Query Statistics](../../Topics\TopicNameNotContainA/Live-Query-Statistics.md)|Displays real\-time statistics about query execution steps. Because this data is available while the query is executing, these execution statistics are extremely useful for debugging query performance issues.|  
|[SQL Trace](../../Topics\TopicNameNotContainA/SQL-Trace.md)|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stored procedures that create, filter, and define tracing:<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](../Topic/sp_trace_create%20\(Transact-SQL\).md)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](../Topic/sp_trace_generateevent%20\(Transact-SQL\).md)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](../Topic/sp_trace_setfilter%20\(Transact-SQL\).md)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)|  
|Error Logs|The Windows application event log provides an overall picture of events occurring on the Windows Server and Windows operating systems as a whole, as well as events in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, and full\-text search. It contains information about events in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is not available elsewhere. You can use the information in the error log to troubleshoot [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\-related problems.|  
|[System Stored Procedures &#40;Transact-SQL&#41;](../Topic/System%20Stored%20Procedures%20\(Transact-SQL\).md)|The following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system stored procedures provide a powerful alternative for many monitoring tasks:<br /><br /> [sp_who &#40;Transact-SQL&#41;](../Topic/sp_who%20\(Transact-SQL\).md):<br />                    Reports snapshot information about current [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] users and processes, including the currently executing statement and whether the statement is blocked.<br /><br /> [sp_lock &#40;Transact-SQL&#41;](../Topic/sp_lock%20\(Transact-SQL\).md):<br />                    Reports snapshot information about locks, including the object ID, index ID, type of lock, and type or resource to which the lock applies.<br /><br /> [sp_spaceused &#40;Transact-SQL&#41;](../Topic/sp_spaceused%20\(Transact-SQL\).md): <br />                    Displays an estimate of the current amount of disk space used by a table \(or a whole database\).<br /><br /> [sp_monitor &#40;Transact-SQL&#41;](../Topic/sp_monitor%20\(Transact-SQL\).md):<br />                    Displays statistics, including CPU usage, I\/O usage, and the amount of time idle since **sp\_monitor** was last executed.|  
|[DBCC &#40;Transact-SQL&#41;](../Topic/DBCC%20\(Transact-SQL\).md)|DBCC \(Database Console Command\) statements enable you to check performance statistics and the logical and physical consistency of a database.|  
|[Built-in Functions &#40;Transact-SQL&#41;](../Topic/Built-in%20Functions%20\(Transact-SQL\).md)|Built\-in functions display snapshot statistics about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] activity since the server was started; these statistics are stored in predefined [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] counters. For example, **@@CPU\_BUSY** contains the amount of time the CPU has been executing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] code; **@@CONNECTIONS** contains the number of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connections or attempted connections; and **@@PACKET\_ERRORS** contains the number of network packets occurring on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connections.|  
|[Trace Flags &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md)|Trace flags display information about a specific activity within the server and are used to diagnose problems or performance issues \(for example, deadlock chains\).|  
|[Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Database-Engine-Tuning-Advisor.md)|Database Engine Tuning Advisor analyzes the performance effects of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements executed against databases you want to tune. Database Engine Tuning Advisor provides recommendations to add, remove, or modify indexes, indexed views, and partitioning.|  
  
## Choosing a Monitoring Tool  
 The choice of a monitoring tool depends on the event or activity to be monitored.  
  
|Event or activity|SQL Server Profiler|Distributed Replay|System Monitor|Activity Monitor|Transact\-SQL|Error logs|  
|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Trend analysis|Yes||Yes||||  
|Replaying captured events|Yes \(From a single computer\)|Yes \(From multiple computers\)|||||  
|Ad hoc monitoring|Yes|||Yes|Yes|Yes|  
|Generating alerts|||Yes||||  
|Graphical interface|Yes||Yes|Yes||Yes|  
|Using within custom application|Yes\*||||Yes||  
  
 \*Using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] system stored procedures.  
  
## Windows Monitoring Tools  
 Windows operating systems and Windows Server 2003 also provide these monitoring tools.  
  
|Tool|Description|  
|----------|-----------------|  
|Task Manager|Shows a synopsis of the processes and applications running on the system.|  
|Network Monitor Agent|Monitors network traffic.|  
  
 For more information about Windows operating systems or Windows Server tools, see the Windows documentation.  
  
  