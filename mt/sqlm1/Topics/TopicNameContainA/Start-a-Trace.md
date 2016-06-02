---
title: Start a Trace
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
---
# Start a Trace
  After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.  
  
## Starting a Trace  
 When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] or [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] creates a queue that provides a temporary holding place for captured server events.  
  
 When you use [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] to access SQL Trace, a new trace window opens \(if one is not already open\) when a trace is started, and data is immediately captured.  
  
 When you use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] starts for data to be captured. When a trace has been started, you can modify only the name of the trace.  
  
> [!NOTE]  
>  When working with existing traces, you can view the properties, but you cannot modify the properties. To modify the properties, stop or pause the trace.  
  
## See Also  
 [Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../Topic/Start%20a%20Trace%20Automatically%20after%20Connecting%20to%20a%20Server%20\(SQL%20Server%20Profiler\).md)   
 [Pause a Trace &#40;SQL Server Profiler&#41;](../Topic/Pause%20a%20Trace%20\(SQL%20Server%20Profiler\).md)   
 [Stop a Trace &#40;SQL Server Profiler&#41;](../Topic/Stop%20a%20Trace%20\(SQL%20Server%20Profiler\).md)   
 [Clear a Trace Window &#40;SQL Server Profiler&#41;](../Topic/Clear%20a%20Trace%20Window%20\(SQL%20Server%20Profiler\).md)   
 [Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;](../Topic/Run%20a%20Trace%20After%20It%20Has%20Been%20Paused%20or%20Stopped%20\(SQL%20Server%20Profiler\).md)  
  
  