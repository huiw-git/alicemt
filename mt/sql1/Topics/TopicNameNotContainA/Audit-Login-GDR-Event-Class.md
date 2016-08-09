---
title: "Audit Login GDR Event Class"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc0560d9-bbb9-4263-a1f3-827c80167f8c
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Audit Login GDR Event Class
The **Audit Login GDR** event class occurs whenever a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login right is added or removed. This event class is for the **sp_grantlogin**, **sp_revokelogin**, and **sp_denylogin** stored procedures.  
  
 This event class may be removed in a future version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. It is recommended that you use the **Audit Server Principal Management** event class instead.  
  
## Audit Login GDR Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|**ClientProcessID**|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client process ID is provided by the client.|9|Yes|  
|**DatabaseID**|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance. [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] displays the name of the database if the **ServerName** data column is captured in the trace and the server is available. Determine the value for a database by using the DB_ID function.|3|Yes|  
|**DatabaseName**|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|**EventClass**|**int**|Type of event = 105.|27|No|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**EventSubClass**|**int**|Type of event subclass.<br /><br /> 1=Grant<br /><br /> 2=Revoke<br /><br /> 3=Deny|21|Yes|  
|**HostName**|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the host name is provided by the client. To determine the host name, use the HOST_NAME function.|8|Yes|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 = system, 0 = user.|60|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login credentials in the form of DOMAIN\username).|11|Yes|  
|**LoginSid**|**image**|Security identification number (SID) of the logged-in user. You can find this information in the **sys.server_principals** catalog view. Each SID is unique for each login in the server.|41|Yes|  
|**NTDomainName**|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|**NTUserName**|**nvarchar**|Windows user name.|6|Yes|  
|**RequestID**|**int**|ID of the request containing the statement.|49|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**Nvarchar**|The login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
|**Success**|**int**|1 = success. 0 = failure. For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.|23|Yes|  
|**TargetLoginName**|**nvarchar**|For actions that target a login (for example, adding a new login), the name of the targeted login.|42|Yes|  
|**TargetLoginSid**|**image**|SID of the targeted login.|43|Yes|  
|**TransactionID**|**bigint**|System-assigned ID of the transaction.|4|Yes|  
|**XactSequence**|**bigint**|Token used to describe the current transaction.|50|Yes|  
  
## See Also  
 [Extended Events](../../Topics/TopicNameNotContainA/Extended-Events.md)   
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [sp_grantlogin (Transact-SQL)](assetId:///0c873d99-c3bf-4eb1-948b-a46cb235ccd4)   
 [sp_revokelogin (Transact-SQL)](assetId:///cb1ab102-1ae0-4811-9144-9a8121ef2d7e)   
 [sp_denylogin (Transact-SQL)](assetId:///db80f152-e8af-4303-95b6-3a3a7b664374)   
 [Audit Server Principal Management Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Principal-Management-Event-Class.md)