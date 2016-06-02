---
title: Create and Run Traces Using Transact-SQL Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
---
# Create and Run Traces Using Transact-SQL Stored Procedures
  The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] or by using system stored procedures.  
  
 As an alternative to [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], you can use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] system stored procedures to create and run traces. The process of tracing by using system stored procedures is as follows:  
  
1.  Create a trace by using **sp\_trace\_create**.  
  
2.  Add events with **sp\_trace\_setevent**.  
  
3.  \(Optional\) Set a filter with **sp\_trace\_setfilter**.  
  
4.  Start the trace with **sp\_trace\_setstatus**.  
  
5.  Stop the trace with **sp\_trace\_setstatus**.  
  
6.  Close the trace with **sp\_trace\_setstatus**.  
  
    > [!NOTE]  
    >  Using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] system stored procedures creates a server\-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur. If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance continues to run, but tracing stops. If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance shuts down. For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../Topics\TopicNameNotContainA/c2-audit-mode-Server-Configuration-Option.md).  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Optimize SQL Trace](../../Topics\TopicNameNotContainA/Optimize-SQL-Trace.md)|Contains information about ways you can reduce the effects of tracing on system performance.|  
|[Filter a Trace](../../Topics\TopicNameContainA/Filter-a-Trace.md)|Contains information about using filters for tracing.|  
|[Limit Trace File and Table Sizes](../../Topics\TopicNameNotContainA/Limit-Trace-File-and-Table-Sizes.md)|Contains information about how to limit the size of files and tables where trace data is written. Note that only [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] can write trace information to tables.|  
|[Schedule Traces](../../Topics\TopicNameNotContainA/Schedule-Traces.md)|Contains information about how to set the start time and the end time for tracing.|  
  
## See Also  
 [sp_trace_create &#40;Transact-SQL&#41;](../Topic/sp_trace_create%20\(Transact-SQL\).md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../Topic/sp_trace_setfilter%20\(Transact-SQL\).md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)  
  
  