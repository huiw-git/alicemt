---
title: Lock:Timeout Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8492f4be-4ea9-4059-80e0-9e7b71597da9
---
# Lock:Timeout Event Class
  The Lock:Timeout event class indicates that a request for a lock on a resource, such as a page, has timed out because another transaction is holding a blocking lock on the required resource. Time\-out is determined by the @@LOCK\_TIMEOUT system function and can be set with the SET LOCK\_TIMEOUT statement.  
  
 Use the Lock:Timeout event class to monitor when time\-out conditions occur. This information is useful to determine if time\-outs are significantly affecting the performance of your application, and which objects are involved. You can examine the application code that modifies these objects to determine if changes to minimize time\-outs can be made.  
  
 Lock:Timeout events with a duration of 0 are commonly the result of internal lock probes and are not necessarily an indication of a problem. The Lock:Timeout \(timeout \> 0\) event can be used to ignore time\-outs with a duration of 0.  
  
## Lock:Timeout Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|BinaryData|**image**|Lock resource identifier.|2|Yes|  
|ClientProcessID|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|DatabaseID|**int**|ID of the database in which the lock time\-out occurred. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the ServerName data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|DatabaseName|**nvarchar**|Name of the database in which the time\-out occurred.|35|Yes|  
|Duration|**bigint**|Amount of time \(in microseconds\) between the time the lock request was issued and the lock was timed out.|13|Yes|  
|EndTime|**datetime**|Time at which the event ended.|15|Yes|  
|EventClass|**int**|Type of event \= 27.|27|No|  
|EventSequence|**int**|The sequence of a given event within the request.|51|No|  
|GroupID|**int**|ID of the workload group where the SQL Trace event fires.|66|Yes|  
|HostName|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|IntegerData2|**int**|[!INCLUDE[ssInternalOnly](../../Token\Other/ssInternalOnly_md.md)]|55|Yes|  
|IsSystem|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|LoginName|**nvarchar**|Name of the login of the user \(either [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\username\).|11|Yes|  
|LoginSid|**image**|Security identification number \(SID\) of the logged\-in user. You can find this information in the sys.server\_principals catalog view. Each SID is unique for each login in the server.|41|Yes|  
|Mode|**int**|The resulting mode after the time\-out.<br /><br /> 0\=NULL \- Compatible with all other lock modes \(LCK\_M\_NL\)<br /><br /> 1\=Schema Stability lock \(LCK\_M\_SCH\_S\)<br /><br /> 2\=Schema Modification Lock \(LCK\_M\_SCH\_M\)<br /><br /> 3\=Shared Lock \(LCK\_M\_S\)<br /><br /> 4\=Update Lock \(LCK\_M\_U\)<br /><br /> 5\=Exclusive Lock \(LCK\_M\_X\)<br /><br /> 6\=Intent Shared Lock \(LCK\_M\_IS\)<br /><br /> 7\=Intent Update Lock \(LCK\_M\_IU\)<br /><br /> 8\=Intent Exclusive Lock \(LCK\_M\_IX\)<br /><br /> 9\=Shared with intent to Update \(LCK\_M\_SIU\)<br /><br /> 10\=Shared with Intent Exclusive \(LCK\_M\_SIX\)<br /><br /> 11\=Update with Intent Exclusive \(LCK\_M\_UIX\)<br /><br /> 12\=Bulk Update Lock \(LCK\_M\_BU\)<br /><br /> 13\=Key range Shared\/Shared \(LCK\_M\_RS\_S\)<br /><br /> 14\=Key range Shared\/Update \(LCK\_M\_RS\_U\)<br /><br /> 15\=Key Range Insert NULL \(LCK\_M\_RI\_NL\)<br /><br /> 16\=Key Range Insert Shared \(LCK\_M\_RI\_S\)<br /><br /> 17\=Key Range Insert Update \(LCK\_M\_RI\_U\)<br /><br /> 18\=Key Range Insert Exclusive \(LCK\_M\_RI\_X\)<br /><br /> 19\=Key Range Exclusive Shared \(LCK\_M\_RX\_S\)<br /><br /> 20\=Key Range Exclusive Update \(LCK\_M\_RX\_U\)<br /><br /> 21\=Key Range Exclusive Exclusive \(LCK\_M\_RX\_X\)|32|Yes|  
|NTDomainName|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|NTUserName|**nvarchar**|Windows user name.|6|Yes|  
|ObjectID|**int**|ID of the object which was timed out, if available and applicable.|22|Yes|  
|ObjectID2|**bigint**|ID of the related object or entity, if available and applicable.|56|Yes|  
|OwnerID|**int**|1\=TRANSACTION<br /><br /> 2\=CURSOR<br /><br /> 3\=SESSION<br /><br /> 4\=SHARED\_TRANSACTION\_WORKSPACE<br /><br /> 5\=EXCLUSIVE\_TRANSACTION\_WORKSPACE|58|Yes|  
|RequestID|**int**|ID of the request containing the statement.|49|Yes|  
|ServerName|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] being traced.|26|No|  
|SessionLoginName|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1; while LoginName shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|SPID|**int**|ID of the session on which the event occurred.|12|Yes|  
|StartTime|**datetime**|Time at which the event started, if available.|14|Yes|  
|TextData|**ntext**|Text value dependent on the lock type that was being acquired when the time\-out occurred.|1|Yes|  
|TransactionID|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
|Type|**int**|1\=NULL\_RESOURCE<br /><br /> 2\=DATABASE<br /><br /> 3\=FILE<br /><br /> 5\=OBJECT<br /><br /> 6\=PAGE<br /><br /> 7\=KEY<br /><br /> 8\=EXTENT<br /><br /> 9\=RID<br /><br /> 10\=APPLICATION<br /><br /> 11\=METADATA<br /><br /> 12\=AUTONAMEDB<br /><br /> 13\=HOBT<br /><br /> 14\=ALLOCATION\_UNIT|57|Yes|  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [Lock:Timeout &#40;timeout &#62; 0&#41; Event Class](../Topic/Lock:Timeout%20\(timeout%20%3E%200\)%20Event%20Class.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../Topic/sys.dm_tran_locks%20\(Transact-SQL\).md)  
  
  