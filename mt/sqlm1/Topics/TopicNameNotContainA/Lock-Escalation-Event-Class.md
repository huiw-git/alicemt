---
title: Lock:Escalation Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d253b44c-7600-4afa-a3a7-03cc937c6a4b
---
# Lock:Escalation Event Class
  The **Lock:Escalation** event class indicates that a finer\-grained lock has been converted to a coarser\-grained lock; for example, a row lock that is converted to an object lock. The escalation event class is Event ID 60.  
  
## Lock:Escalation Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|**ClientProcessID**|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|**DatabaseID**|**int**|ID of the database in which the lock was acquired. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the **ServerName** data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|**DatabaseName**|**nvarchar**|Name of the database in which the escalation occurred.|35|Yes|  
|**EventClass**|**int**|Type of event \= 60.|27|No|  
|**EventSubClass**|**int**|Cause of the lock escalation:<br /><br /> **0 \- LOCK\_THRESHOLD** indicates the statement exceeded the lock threshold.<br /><br /> **1 \- MEMORY\_THRESHOLD** indicates the statement exceeded the memory threshold.|21|Yes|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**GroupID**|**int**|ID of the workload group where the SQL Trace event fires.|66|Yes|  
|**HostName**|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|**IntegerData**|**int**|HoBT lock count. The number of locks for the HoBT at the time of lock escalation.|25|Yes|  
|**IntegerData2**|**int**|Escalated lock count. The total number of locks that were converted. These lock structures are deallocated because they are already covered by the escalated lock.|55|Yes|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|**LineNumber**|**int**|Line number of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement.|5|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user \(either [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\username\).|11|Yes|  
|**LoginSid**|**image**|Security identification number \(SID\) of the logged\-in user. You can find this information in the **sys.server\_principals** catalog view. Each SID is unique for each login in the server.|41|Yes|  
|**Mode**|**int**|Resulting lock mode after the escalation:<br /><br /> 0\=NULL \- Compatible with all other lock modes \(LCK\_M\_NL\)<br /><br /> 1\=Schema Stability lock \(LCK\_M\_SCH\_S\)<br /><br /> 2\=Schema Modification Lock \(LCK\_M\_SCH\_M\)<br /><br /> 3\=Shared Lock \(LCK\_M\_S\)<br /><br /> 4\=Update Lock \(LCK\_M\_U\)<br /><br /> 5\=Exclusive Lock \(LCK\_M\_X\)<br /><br /> 6\=Intent Shared Lock \(LCK\_M\_IS\)<br /><br /> 7\=Intent Update Lock \(LCK\_M\_IU\)<br /><br /> 8\=Intent Exclusive Lock \(LCK\_M\_IX\)<br /><br /> 9\=Shared with intent to Update \(LCK\_M\_SIU\)<br /><br /> 10\=Shared with Intent Exclusive \(LCK\_M\_SIX\)<br /><br /> 11\=Update with Intent Exclusive \(LCK\_M\_UIX\)<br /><br /> 12\=Bulk Update Lock \(LCK\_M\_BU\)<br /><br /> 13\=Key range Shared\/Shared \(LCK\_M\_RS\_S\)<br /><br /> 14\=Key range Shared\/Update \(LCK\_M\_RS\_U\)<br /><br /> 15\=Key Range Insert NULL \(LCK\_M\_RI\_NL\)<br /><br /> 16\=Key Range Insert Shared \(LCK\_M\_RI\_S\)<br /><br /> 17\=Key Range Insert Update \(LCK\_M\_RI\_U\)<br /><br /> 18\=Key Range Insert Exclusive \(LCK\_M\_RI\_X\)<br /><br /> 19\=Key Range Exclusive Shared \(LCK\_M\_RX\_S\)<br /><br /> 20\=Key Range Exclusive Update \(LCK\_M\_RX\_U\)<br /><br /> 21\=Key Range Exclusive Exclusive \(LCK\_M\_RX\_X\)|32|Yes|  
|**NTDomainName**|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|**NTUserName**|**nvarchar**|Windows user name.|6|Yes|  
|**ObjectID**|**int**|System\-assigned ID of the table for which lock escalation was triggered.|22|Yes|  
|**ObjectID2**|**bigint**|ID of the related object or entity. \(HoBT ID for which the lock escalation was triggered.\)|56|Yes|  
|**Offset**|**int**|Starting offset of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement.|61|Yes|  
|**OwnerID**|**int**|1\=TRANSACTION<br /><br /> 2\=CURSOR<br /><br /> 3\=SESSION<br /><br /> 4\=SHARED\_TRANSACTION\_WORKSPACE<br /><br /> 5\=EXCLUSIVE\_TRANSACTION\_WORKSPACE<br /><br /> 6\=WAITFOR\_QUERY|58|Yes|  
|**RequestID**|**int**|ID of the request containing the statement.|49|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
|**TextData**|**ntext**|Text of the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that caused lock escalation.|1|Yes|  
|**TransactionID**|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
|**Type**|**int**|Lock escalation granularity:<br /><br /> 1\=NULL\_RESOURCE<br /><br /> 2\=DATABASE<br /><br /> 3\=FILE<br /><br /> 5\=OBJECT \(table level\)<br /><br /> 6\=PAGE<br /><br /> 7\=KEY<br /><br /> 8\=EXTENT<br /><br /> 9\=RID<br /><br /> 10\=APPLICATION<br /><br /> 11\=METADATA<br /><br /> 12\=HOBT<br /><br /> 13\=ALLOCATION\_UNIT|57|Yes|  
  
## Examples  
 The following example uses the `sp_trace_create` procedure to create a trace, uses `sp_trace_setevent` to add lock escalation columns to the trace, and then uses `sp_trace_setstatus` to start the trace. In statements such as `EXEC sp_trace_setevent @TraceID, 60, 22, 1`, the number `60` indicates the escalation event class, `22` indicates the **ObjectID** column, and `1` sets the trace event to ON.  
  
```  
DECLARE @RC int, @TraceID int;  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\TraceResults';  
-- Set the events and data columns you need to capture.  
EXEC sp_trace_setevent @TraceID, 60,  1, 1; --  1 = TextData  
EXEC sp_trace_setevent @TraceID, 60, 12, 1; -- 12 = SPID  
EXEC sp_trace_setevent @TraceID, 60, 21, 1; -- 21 = EventSubClass  
EXEC sp_trace_setevent @TraceID, 60, 22, 1; -- 22 = ObjectID  
EXEC sp_trace_setevent @TraceID, 60, 25, 1; -- 25 = IntegerData  
EXEC sp_trace_setevent @TraceID, 60, 55, 1; -- 25 = IntegerData2  
EXEC sp_trace_setevent @TraceID, 60, 57, 1; -- 57 = Type  
-- Set any filter  byusing sp_trace_setfilter.  
-- Start the trace.  
EXEC sp_trace_setstatus @TraceID, 1;  
GO  
```  
  
 Now that the trace is running, execute the statements that you want to trace. When they finish, execute the following code to stop and then close the trace. This example uses the `fn_trace_getinfo` function to get the `traceid` to be used in the `sp_trace_setstatus` statements.  
  
```  
-- After the trace is complete.  
DECLARE @TraceID int;  
-- Find the traceid of the current trace.  
SELECT @TraceID = traceid   
FROM ::fn_trace_getinfo(default)   
WHERE value = N'C:\TraceResults.trc';  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0;  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2;  
GO  
```  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../Topic/sys.dm_tran_locks%20\(Transact-SQL\).md)  
  
  