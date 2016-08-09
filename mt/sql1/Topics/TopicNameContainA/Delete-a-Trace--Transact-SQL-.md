---
title: "Delete a Trace (Transact-SQL)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Delete a Trace (Transact-SQL)
This topic describes how to use stored procedures to delete a trace.  
  
 For an example of using trace stored procedures, see [Create a Trace (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Trace--Transact-SQL-.md).  
  
### To delete a trace  
  
1.  Execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.  
  
2.  Execute **sp_trace_setstatus** by specifying **@status = 2** to close the trace and delete its information from the server.  
  
> [!NOTE]  
>  A trace must be stopped first before it can be closed.  
  
## See Also  
 [SQL Server Profiler Stored Procedures (Transact-SQL)](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)   
 [System Stored Procedures](assetId:///a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a)   
 [SQL Profiler Stored Procedures (Transact-SQL)](assetId:///8c99c3db-0b04-46c3-aa59-d6f680522fdd)