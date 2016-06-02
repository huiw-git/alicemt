---
title: Audit Change Database Owner Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f1dd4fc-2540-423c-80ad-c5bc712c42e0
---
# Audit Change Database Owner Event Class
  The **Audit Change Database Owner** event class occurs when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions required to do that are checked.  
  
## Audit Change Database Owner Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|**ClientProcessID**|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|**DatabaseID**|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the **ServerName** data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|**DatabaseName**|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|**DBUserName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] user name of the client.|40|Yes|  
|**EventClass**|**int**|Type of event \= 152.|27|No|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**HostName**|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user \(either the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\username\).|11|Yes|  
|**LoginSid**|**image**|Security identification number \(SID\) of the logged\-in user. You can find this information in the **sys.server\_principals** catalog view. Each SID is unique for each login in the server.|41|Yes|  
|**NTDomainName**|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|**NTUserName**|**nvarchar**|Windows user name.|6|Yes|  
|**RequestID**|**int**|ID of the request containing the statement.|49|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the even occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
|**Success**|**int**|1 \= success. 0 \= failure. For example, a value of 1 indicates success of a permissions check and a value of 0 indicates a failure of that check\).|23|Yes|  
|**TargetLoginName**|**nvarchar**|For actions that target a login, the name of the targeted login.|42|Yes|  
|**TargetLoginSid**|**image**|For actions that target a login, the security identification number \(SID\) of the targeted login.|43|Yes|  
|**TargetUserName**|**nvarchar**|For actions that target a database user \(for example, granting permission to a user\), the name of that user.|39|Yes|  
|**TransactionID**|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
|**XactSequence**|**bigint**|Token used to describe the current transaction.|50|Yes|  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../Topic/ALTER%20AUTHORIZATION%20\(Transact-SQL\).md)  
  
  