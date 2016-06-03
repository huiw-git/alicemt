---
title: Set a Trace Filter (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
---
# Set a Trace Filter (Transact-SQL)
  This topic describes how to use stored procedures to create a filter that retrieves only the information you need on an event being traced.  
  
### To set a trace filter  
  
1.  If the trace is already running, execute **sp\_trace\_setstatus** by specifying **@status \= 0** to stop the trace.  
  
2.  Execute **sp\_trace\_setfilter** to configure the type of information to retrieve for the event being traced.  
  
> [!IMPORTANT]  
>  Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] stored procedures \(**sp\_trace\_*xx***\) are strictly typed and do not support automatic data type conversion. If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure will return an error.  
  
## See Also  
 [Filter a Trace](../../Topics\TopicNameContainA/Filter-a-Trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../Topic/sp_trace_setfilter%20\(Transact-SQL\).md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../Topic/sp_trace_setstatus%20\(Transact-SQL\).md)   
 [System Stored Procedures &#40;Transact-SQL&#41;](../Topic/System%20Stored%20Procedures%20\(Transact-SQL\).md)   
 [SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](../Topic/SQL%20Server%20Profiler%20Stored%20Procedures%20\(Transact-SQL\).md)  
  
  