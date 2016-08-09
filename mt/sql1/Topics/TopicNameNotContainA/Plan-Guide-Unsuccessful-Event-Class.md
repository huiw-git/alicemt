---
title: "Plan Guide Unsuccessful Event Class"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef9759f8-5613-4884-9257-86b609313f69
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Plan Guide Unsuccessful Event Class
The Plan Guide Unsuccessful event class indicates that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] could not produce an execution plan for a query or batch that contained a plan guide. Instead, the plan was compiled without using the plan guide. The event fires when the following conditions are true:  
  
-   The batch/module in the plan guide definition matches the batch that is being executed.  
  
-   The query in the plan guide definition matches the query that is being executed.  
  
-   The hints in the plan guide definition, including the USE PLAN hint, were not applied successfully to the query or batch. That is, the compiled query plan could not honor the specified hints and the plan was compiled without using the plan guide.  
  
 An invalid plan guide might cause this event to fire. Validate the plan guide that is used by the query or batch by using the [sys.fn_validate_plan_guide](assetId:///3af8b47a-936d-4411-91d1-d2d16dda5623) function, and correct the error that is reported by this function.  
  
 This event is included in the [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] Tuning template.  
  
## Plan Guide Unsuccessful Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This column is populated with the values that are passed by the application instead of the displayed name of the program.|10|Yes|  
|ClientProcessID|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|DatabaseID|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a specified instance. [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] displays the name of the database if the ServerName data column is captured in the trace and the server is available. Determine the value for a database by using the DB_ID function.|3|Yes|  
|DatabaseName|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|EventClass|**int**|Type of event = 218.|27|No|  
|EventSequence|**int**|Sequence of a specific event within the request.|51|No|  
|HostName|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST_NAME function.|8|Yes|  
|IsSystem|**int**|Indicates whether the event occurred on a system process or a user process: 1 = system, 0 = user.|60|Yes|  
|LoginName|**nvarchar**|Name of the login of the user (either [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\*username*).|11|Yes|  
|LoginSid|**image**|Security identification number (SID) of the logged-in user. You can find this information in the [sys.server_principals](assetId:///c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37) or the [sys.sql_logins](assetId:///0d9c5b09-86fe-40ff-baab-00b7c051402f) catalog views. Each SID is unique for each login in the server.|41|Yes|  
|NTDomainName|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|NTUserName|**nvarchar**|Windows user name.|6|Yes|  
|ObjectID|**int**|Object ID of the module that was being compiled when the plan guide was applied. If the plan guide was not applied to a module, this column is set to NULL.|22|Yes|  
|RequestID|**int**|ID of the request that is containing the statement.|49|Yes|  
|ServerName|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is being traced.|26|No|  
|SessionLoginName|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|SPID|**int**|ID of the session on which the event occurred.|12|Yes|  
|StartTime|**datetime**|Time at which the event started, if available.|14|Yes|  
|TextData|**ntext**|Name of the plan guide.|1|Yes|  
|TransactionID|**bigint**|System-assigned ID of the transaction.|4|Yes|  
|XactSequence|**bigint**|Token that describes the current transaction.|50|Yes|  
  
## See Also  
 [Plan Guide Successful Event Class](../../Topics/TopicNameNotContainA/Plan-Guide-Successful-Event-Class.md)   
 [Extended Events](../../Topics/TopicNameNotContainA/Extended-Events.md)   
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [sys.fn_validate_plan_guide (Transact-SQL)](assetId:///3af8b47a-936d-4411-91d1-d2d16dda5623)   
 [sp_create_plan_guide (Transact-SQL)](assetId:///5a8c8040-4f96-4c74-93ab-15bdefd132f0)   
 [sp_create_plan_guide_from_cache (Transact-SQL)](assetId:///02cfb76f-a0f9-4b42-a880-1c3e7d64fe41)