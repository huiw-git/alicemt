---
title: Plan Guide Successful Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fecfbb6c-56c9-4db4-84d3-00d6e338355a
---
# Plan Guide Successful Event Class
  The Plan Guide Successful event class indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] successfully produced an execution plan for a query or batch that contained a plan guide. The event fires when the following conditions are true:  
  
-   The batch or module in the plan guide definition matches the batch or module that is being executed.  
  
-   The query in the plan guide definition matches the query being executed.  
  
-   The hints in the plan guide definition, including the USE PLAN hint, were applied successfully to the query. That is, the compiled query plan honors the specified hints.  
  
## Plan Guide Successful Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values that are passed by the application instead of the displayed name of the program.|10|Yes|  
|ClientProcessID|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|DatabaseID|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a specified instance. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the ServerName data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|DatabaseName|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|EventClass|**int**|Type of event \= 214.|27|No|  
|EventSequence|**int**|Sequence of a specific event within the request.|51|No|  
|HostName|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|IsSystem|**int**|Indicates whether the event occurred on a system process or a user process: 1 \= system, 0 \= user.|60|Yes|  
|LoginName|**nvarchar**|Name of the login of the user \(either [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\*username*\).|11|Yes|  
|LoginSid|**image**|Security identification number \(SID\) of the logged\-in user. You can find this information in the [sys.server\_principals](../Topic/sys.server_principals%20\(Transact-SQL\).md) or the [sys.sql\_logins](../Topic/sys.sql_logins%20\(Transact-SQL\).md) catalog views. Each SID is unique for each login in the server.|41|Yes|  
|NTDomainName|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|NTUserName|**nvarchar**|Windows user name.|6|Yes|  
|ObjectID|**int**|Object ID of the module that was being compiled when the plan guide was applied. If the plan guide was not applied to a module, this column is set to NULL.|22|Yes|  
|RequestID|**int**|ID of the request that contains the statement.|49|Yes|  
|ServerName|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is being traced.|26|No|  
|SessionLoginName|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|SPID|**int**|ID of the session on which the event occurred.|12|Yes|  
|StartTime|**datetime**|Time at which the event started, if available.|14|Yes|  
|TextData|**ntext**|Name of the plan guide.|1|Yes|  
|TransactionID|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
|XactSequence|**bigint**|Token that describes the current transaction.|50|Yes|  
  
## See Also  
 [Plan Guide Unsuccessful Event Class](../../Topics\TopicNameNotContainA/Plan-Guide-Unsuccessful-Event-Class.md)   
 [Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)  
  
  