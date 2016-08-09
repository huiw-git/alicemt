---
title: "default trace enabled Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# default trace enabled Server Configuration Option
Use the **default trace enabled** option to enable or disable the default trace log files. The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)] Use Extended Events instead.  
  
## Purpose  
 Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.  
  
## Viewing  
 The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] or queried with [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] by using the `fn_trace_gettable` system function. [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] can open the default trace log files just as it does normal trace output files. The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file. The base file name for the default trace log file is `log.trc`. In a typical installation of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the default trace is enabled and thus becomes TraceID 1. If enabled after installation and after creating other traces, the TraceID can become a larger number.  
  
 For more information about using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Profiler to view this trace file, see [Open a Trace File (SQL Server Profiler)](../../Topics/TopicNameContainA/Open-a-Trace-File--SQL-Server-Profiler-.md)  
  
### Example:  
 The following statement opens the default trace log in the default location:  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## Configuring  
 When set to 1, the **default trace enabled** option enables **Default Trace**. The default setting for this option is 1 (ON). A value of 0 turns off the trace.  
  
 The **default trace enabled** option is an advanced option. If you are using the **sp_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1. The setting takes effect immediately without a server restart.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)