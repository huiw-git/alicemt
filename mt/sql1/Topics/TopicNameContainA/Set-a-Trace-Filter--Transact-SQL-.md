---
title: "Set a Trace Filter (Transact-SQL)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Set a Trace Filter (Transact-SQL)
This topic describes how to use stored procedures to create a filter that retrieves only the information you need on an event being traced.  
  
### To set a trace filter  
  
1.  If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.  
  
2.  Execute **sp_trace_setfilter** to configure the type of information to retrieve for the event being traced.  
  
> [!IMPORTANT]  
>  Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] stored procedures (**sp_trace_*xx***) are strictly typed and do not support automatic data type conversion. If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure will return an error.  
  
## See Also  
 [Filter a Trace](../../Topics/TopicNameContainA/Filter-a-Trace.md)   
 [sp_trace_setfilter](assetId:///11e7c7ac-a581-4a64-bb15-9272d5c1f7ac)   
 [sp_trace_setstatus](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)   
 [System Stored Procedures](assetId:///a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a)   
 [SQL Profiler Stored Procedures (Transact-SQL)](assetId:///8c99c3db-0b04-46c3-aa59-d6f680522fdd)