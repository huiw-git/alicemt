---
title: Start a Trace
H1: na
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
  After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/includes/ssSqlProfiler_md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.  
  
## Starting a Trace  
 When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)] or [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)], [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] creates a queue that provides a temporary holding place for captured server events.  
  
 When you use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/includes/ssSqlProfiler_md.md)] to access SQL Trace, a new trace window opens (if one is not already open) when a trace is started, and data is immediately captured.  
  
 When you use [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] starts for data to be captured. When a trace has been started, you can modify only the name of the trace.  
  
> [!NOTE]  
>  When working with existing traces, you can view the properties, but you cannot modify the properties. To modify the properties, stop or pause the trace.  
  
## See Also  
 [Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Start-a-Trace-Automatically-after-Connecting-to-a-Server--SQL-Server-Profiler-.md)   
 [Pause a Trace &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Pause-a-Trace--SQL-Server-Profiler-.md)   
 [Stop a Trace &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Stop-a-Trace--SQL-Server-Profiler-.md)   
 [Clear a Trace Window &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Clear-a-Trace-Window--SQL-Server-Profiler-.md)   
 [Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;](../../Topics/TopicNameContainA/Run-a-Trace-After-It-Has-Been-Paused-or-Stopped--SQL-Server-Profiler-.md)  
  
  