---
title: "Schedule Traces"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Schedule Traces
There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You can:  
  
-   Enable a trace stop time.  
  
-   Use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent to schedule a trace.  
  
## Specifying a Stop Time  
 You can specify a trace stop time if you use [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)]. The stop time must be set when the trace is originally configured.  
  
## Scheduling Traces by Using SQL Server Agent  
 The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)].  
  
 **To set an end time filter for a trace**  
  
 [Filter Events Based on the Event End Time (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Filter-Events-Based-on-the-Event-End-Time--SQL-Server-Profiler-.md)  
  
 [Using Transact-SQL](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)  
  
## See Also  
 [Automating Administrative Tasks (SQL Server Agent)](assetId:///541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)