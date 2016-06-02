---
title: default trace enabled Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
---
# default trace enabled Server Configuration Option
  Use the **default trace enabled** option to enable or disable the default trace log files. The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)] Use Extended Events instead.  
  
## Purpose  
 Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.  
  
## Viewing  
 The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] or queried with [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] by using the `fn_trace_gettable` system function. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] can open the default trace log files just as it does normal trace output files. The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file. The base file name for the default trace log file is `log.trc`. In a typical installation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the default trace is enabled and thus becomes TraceID 1. If enabled after installation and after creating other traces, the TraceID can become a larger number.  
  
 For more information about using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Profiler to view this trace file, see [Open a Trace File &#40;SQL Server Profiler&#41;](../Topic/Open%20a%20Trace%20File%20\(SQL%20Server%20Profiler\).md)  
  
### Example:  
 The following statement opens the default trace log in the default location:  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## Configuring  
 When set to 1, the **default trace enabled** option enables **Default Trace**. The default setting for this option is 1 \(ON\). A value of 0 turns off the trace.  
  
 The **default trace enabled** option is an advanced option. If you are using the **sp\_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1. The setting takes effect immediately without a server restart.  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  