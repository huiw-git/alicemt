---
title: SQL Server Profiler - Replay Configuration (Basic Replay Options)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
---
# SQL Server Profiler - Replay Configuration (Basic Replay Options)
  In the **Replay Configuration** dialog box, use the **Basic Replay Options** page to specify how to replay a trace file or table.  
  
 To view this window, use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to open a trace file or table that contains the appropriate events for replay. For more information, see [Replay Requirements](../../Topics\TopicNameNotContainA/Replay-Requirements.md). While the trace file or table is open, on the **Replay** menu, click **Start**, and then connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where you want to replay the trace.  
  
## Options  
 **Replay server**  
 Displays the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to connect to for the replay.  
  
 **Change...**  
 Launches the **Connect to Server** dialog box to connect to another server.  
  
 **Save to file**  
 Save the replay results to a file. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the standard file dialog, where you can specify the location to save the file.  
  
 **Save to table**  
 Save the replay results to a table. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the table selection dialog, where you can specify the location to save the table.  
  
 **Number of replay threads**  
 Specify the number of replay threads to use concurrently. A higher number consumes more resources during replay, but replay is faster and more concurrent.  
  
 **Replay events in the order they were traced**  
 Replay events sequentially. Use this option if you are replaying a trace for debugging.  
  
 **Replay events using multiple threads**  
 Replay events concurrently. This option is faster than replaying events sequentially, but disables debugging. The events are ordered within their system process identifiers \(SPID\).  
  
 **Display replay results**  
 Display replay results in [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)].  
  
## See Also  
 [Replay a Trace Table &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20Table%20\(SQL%20Server%20Profiler\).md)   
 [Replay a Trace File &#40;SQL Server Profiler&#41;](../Topic/Replay%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)   
 [Replay Traces](../../Topics\TopicNameNotContainA/Replay-Traces.md)  
  
  