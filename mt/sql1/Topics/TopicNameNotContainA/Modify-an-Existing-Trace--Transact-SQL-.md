---
title: "Modify an Existing Trace (Transact-SQL)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Modify an Existing Trace (Transact-SQL)
This topic describes how to use stored procedures to modify an existing trace.  
  
### To modify an existing trace  
  
1.  If the trace is already running, execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.  
  
2.  To modify trace events, execute **sp_trace_setevent** by specifying the changes through the parameters. Listed in order, the parameters are:  
  
    -   **@traceid** (Trace ID)  
  
    -   **@eventid** (Event ID)  
  
    -   **@columnid** (Column ID)  
  
    -   **@on** (ON)  
  
     When you modify the **@on** parameter, keep in mind its interaction with the **@columnid** parameter:  
  
    |ON|Column ID|Result|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|Event is turned on. All columns are cleared.|  
    ||NOT NULL|Column is turned on for the specified event.|  
    |OFF (**0**)|NULL|Event is turned off. All columns are cleared.|  
    ||NOT NULL|Column is turned off for the specified event.|  
  
> [!IMPORTANT]  
>  Unlike regular stored procedures, parameters of all [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] stored procedures (**sp_trace_*xx***) are strictly typed and do not support automatic data type conversion. If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.  
  
## See Also  
 [SQL Server Profiler Stored Procedures (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [sp_trace_setstatus (Transact-SQL)](assetId:///29e7a7d7-b9c1-414a-968a-fc247769750d)   
 [System Stored Procedures](assetId:///a5c4d5b8-5a24-4a2d-99b4-d003b546ee3a)   
 [SQL Server Profiler Stored Procedures (Transact-SQL)](assetId:///8c99c3db-0b04-46c3-aa59-d6f680522fdd)