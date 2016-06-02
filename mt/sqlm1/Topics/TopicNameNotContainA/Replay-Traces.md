---
title: Replay Traces
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
---
# Replay Traces
  Replay is the ability to reproduce activity that has been captured in a trace. When you create or edit a trace, you can save the trace to a file and replay it later. You can use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to replay trace activity from a single computer. For large workloads, use the Distributed Replay Utility to replay trace data from multiple computers.  
  
 This section describes how to use the replay features of [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)]. For more information about the Distributed Replay Utility, see [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md).  
  
 [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. Replay is useful to troubleshoot an application or process problem. When you have identified the problem and implemented corrections, run the trace that found the potential problem against the corrected application or process. Then, replay the original trace and compare results.  
  
 Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] **Replay** menu. These options especially improve the analysis of long scripts because they can break the replay of the trace into short segments so they can be analyzed incrementally.  
  
 For information about the permissions required to replay traces, see [Permissions Required to Run SQL Server Profiler](../../Topics\TopicNameNotContainA/Permissions-Required-to-Run-SQL-Server-Profiler.md).  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md)|Describes the events that must be included in a trace definition so that it can be replayed with [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].|  
|[Replay Options &#40;SQL Server Profiler&#41;](../Topic/Replay%20Options%20\(SQL%20Server%20Profiler\).md)|Describes the options you can set in the **Replay Configuration** dialog box of [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].|  
|[Considerations for Replaying Traces &#40;SQL Server Profiler&#41;](../Topic/Considerations%20for%20Replaying%20Traces%20\(SQL%20Server%20Profiler\).md)|Describes trace events that can not be replayed with [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] and the effects on server performance of replaying traces.|  
  
## See Also  
 [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md)  
  
  