---
title: "Create Manual Traces using Stored Procedures"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create Manual Traces using Stored Procedures
Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]. These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)]. This allows you to write custom applications specific to the needs of your enterprise.  
  
## In This Section  
 The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)].  
  
|Stored procedure|Task performed|  
|----------------------|--------------------|  
|[fn_trace_geteventinfo](assetId:///5b1c858a-ca43-4e2b-9d67-8654daaf0cc5)|Returns information about events included in a trace.|  
|[fn_trace_getinfo](assetId:///04b140fe-110a-47b8-98b5-e4c161beb6c9)|Returns information about a specified trace or all existing traces.|  
|[sp_trace_create](assetId:///f3a43597-4c5a-4520-bcab-becdbbf81d2e)|Creates a trace definition. The new trace will be in a stopped state.|  
|[sp_trace_generateevent](assetId:///3ef05bfb-b467-4403-89cc-6e77ef9247dd)|Creates a user-defined event.|  
|[sp_trace_setevent](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)|Adds an event class or data column to a trace, or removes one from it.|  
|[sp_trace_setstatus](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)|Starts, stops, or closes a trace.|  
|[fn_trace_getfilterinfo](assetId:///09fe4a28-ff8a-4655-9da1-4654d5bc514d)|Returns information about filters applied to a trace.|  
|[sp_trace_setfilter](assetId:///11e7c7ac-a581-4a64-bb15-9272d5c1f7ac)|Applies a new or modified filter to a trace.|  
  
 **To define your own trace using stored procedures**  
  
1.  Specify the events to capture using **sp_trace_setevent**.  
  
2.  Specify any event filters. For more information, see [Set a Trace Filter (Transact-SQL)](../../Topics/TopicNameContainA/Set-a-Trace-Filter--Transact-SQL-.md).  
  
3.  Specify the destination for the captured event data using **sp_trace_create**.  
  
 For an example of using trace stored procedures, see [Create a Trace (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Trace--Transact-SQL-.md).  
  
 **To set trace definition defaults**  
  
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/Set-Trace-Definition-Defaults--SQL-Server-Profiler-.md)  
  
 **To set trace display defaults**  
  
 [SQL Server Profiler](../../Topics/TopicNameNotContainA/Set-Trace-Display-Defaults--SQL-Server-Profiler-.md)  
  
 **To create a trace**  
  
 [SQL Server Profiler](../../Topics/TopicNameContainA/Create-a-Trace--SQL-Server-Profiler-.md)  
  
 [Transact-SQL](../../Topics/TopicNameContainA/Create-a-Trace--Transact-SQL-.md)  
  
 **To add or remove events from a trace template**  
  
 [SQL Server Profiler](../../Topics/TopicNameContainA/Specify-Events-and-Data-Columns-for-a-Trace-File--SQL-Server-Profiler-.md)  
  
 [Transact-SQL](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)