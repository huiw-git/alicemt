---
title: "Create and Run Traces Using Transact-SQL Stored Procedures"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Create and Run Traces Using Transact-SQL Stored Procedures
The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] or by using system stored procedures.  
  
 As an alternative to [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)], you can use [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] system stored procedures to create and run traces. The process of tracing by using system stored procedures is as follows:  
  
1.  Create a trace by using **sp_trace_create**.  
  
2.  Add events with **sp_trace_setevent**.  
  
3.  (Optional) Set a filter with **sp_trace_setfilter**.  
  
4.  Start the trace with **sp_trace_setstatus**.  
  
5.  Stop the trace with **sp_trace_setstatus**.  
  
6.  Close the trace with **sp_trace_setstatus**.  
  
    > [!NOTE]  
    >  Using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] system stored procedures creates a server-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur. If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance continues to run, but tracing stops. If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance shuts down. For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../Topics/TopicNameNotContainA/c2-audit-mode-Server-Configuration-Option.md).  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Optimize SQL Trace](../../Topics/TopicNameNotContainA/Optimize-SQL-Trace.md)|Contains information about ways you can reduce the effects of tracing on system performance.|  
|[Filter a Trace](../../Topics/TopicNameContainA/Filter-a-Trace.md)|Contains information about using filters for tracing.|  
|[Limit Trace File and Table Sizes](../../Topics/TopicNameNotContainA/Limit-Trace-File-and-Table-Sizes.md)|Contains information about how to limit the size of files and tables where trace data is written. Note that only [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] can write trace information to tables.|  
|[Schedule Traces](../../Topics/TopicNameNotContainA/Schedule-Traces.md)|Contains information about how to set the start time and the end time for tracing.|  
  
## See Also  
 [sp_trace_create (Transact-SQL)](assetId:///f3a43597-4c5a-4520-bcab-becdbbf81d2e)   
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [sp_trace_setfilter (Transact-SQL)](assetId:///11e7c7ac-a581-4a64-bb15-9272d5c1f7ac)   
 [sp_trace_setstatus (Transact-SQL)](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)