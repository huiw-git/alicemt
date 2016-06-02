---
title: Create Manual Traces using Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
---
# Create Manual Traces using Stored Procedures
  Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)]. This allows you to write custom applications specific to the needs of your enterprise.  
  
## In This Section  
 The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
|Stored procedure|Task performed|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../Topic/sys.fn_trace_geteventinfo%20\(Transact-SQL\).md)|Returns information about events included in a trace.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../Topic/sys.fn_trace_getinfo%20\(Transact-SQL\).md)|Returns information about a specified trace or all existing traces.|  
|[sp_trace_create &#40;Transact-SQL&#41;](../Topic/sp_trace_create%20\(Transact-SQL\).md)|Creates a trace definition. The new trace will be in a stopped state.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](../Topic/sp_trace_generateevent%20\(Transact-SQL\).md)|Creates a user\-defined event.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)|Adds an event class or data column to a trace, or removes one from it.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)|Starts, stops, or closes a trace.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../Topic/sys.fn_trace_getfilterinfo%20\(Transact-SQL\).md)|Returns information about filters applied to a trace.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../Topic/sp_trace_setfilter%20\(Transact-SQL\).md)|Applies a new or modified filter to a trace.|  
  
 **To define your own trace using stored procedures**  
  
1.  Specify the events to capture using **sp\_trace\_setevent**.  
  
2.  Specify any event filters. For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../Topic/Set%20a%20Trace%20Filter%20\(Transact-SQL\).md).  
  
3.  Specify the destination for the captured event data using **sp\_trace\_create**.  
  
 For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../Topic/Create%20a%20Trace%20\(Transact-SQL\).md).  
  
 **To set trace definition defaults**  
  
 [SQL Server Profiler](../Topic/Set%20Trace%20Definition%20Defaults%20\(SQL%20Server%20Profiler\).md)  
  
 **To set trace display defaults**  
  
 [SQL Server Profiler](../Topic/Set%20Trace%20Display%20Defaults%20\(SQL%20Server%20Profiler\).md)  
  
 **To create a trace**  
  
 [SQL Server Profiler](../Topic/Create%20a%20Trace%20\(SQL%20Server%20Profiler\).md)  
  
 [Transact\-SQL](../Topic/Create%20a%20Trace%20\(Transact-SQL\).md)  
  
 **To add or remove events from a trace template**  
  
 [SQL Server Profiler](../Topic/Specify%20Events%20and%20Data%20Columns%20for%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
 [Transact\-SQL](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)  
  
  