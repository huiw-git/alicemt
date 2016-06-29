---
title: Schedule Traces
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
---
# Schedule Traces
  There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. You can:  
  
-   Enable a trace stop time.  
  
-   Use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent to schedule a trace.  
  
## Specifying a Stop Time  
 You can specify a trace stop time if you use [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/includes/ssSqlProfiler_md.md)]. The stop time must be set when the trace is originally configured.  
  
## Scheduling Traces by Using SQL Server Agent  
 The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/includes/ssSqlProfiler_md.md)].  
  
 **To set an end time filter for a trace**  
  
 [Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;](../../Topics/TopicNameNotContainA/Filter-Events-Based-on-the-Event-End-Time--SQL-Server-Profiler-.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)  
  
## See Also  
 [Automated Administration Tasks &#40;SQL Server Agent&#41;](../Topic/Automated%20Administration%20Tasks%20\(SQL%20Server%20Agent\).md)  
  
  