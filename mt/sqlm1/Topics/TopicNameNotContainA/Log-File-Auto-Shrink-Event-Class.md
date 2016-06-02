---
title: Log File Auto Shrink Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bf82a13-9985-4f20-9ef8-0083f104d124
---
# Log File Auto Shrink Event Class
  The **Log File Auto Shrink** event class indicates that the log file shrank automatically. This event is not triggered if the log file shrinks because of an explicit ALTER DATABASE statement.  
  
 Include the **Log File Auto Shrink** event class in traces that monitor the shrinking of the log file. When thisevent class is included in a trace the amount of overhead incurred will be low unless the file frequently shrinks.  
  
## Log File Auto Shrink Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|**ClientProcessID**|**Int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|**DatabaseID**|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the **ServerName** data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|**DatabaseName**|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|**Duration**|**bigint**|Length of time \(in milliseconds\) necessary to extend the file.|13|Yes|  
|**EndTime**|**datetime**|Time that the log file **Auto Shrink** ended.|18|Yes|  
|**EventClass**|**int**|Type of event \= 95.|27|No|  
|**EventSequence**|**int**|Sequence of the **CursorClose** event class in the batch.|51|No|  
|**Filename**|**nvarchar**|Logical name of the file being extended.|36|Yes|  
|**HostName**|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|**IntegerData**|**Int**|Number of 8\-kilobyte \(KB\) pages by which the file increased.|25|Yes|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user \(either [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\Username\).|11|Yes|  
|**LoginSid**|**image**|Security identifier \(SID\) of the logged\-in user. You can find this information in the **sys.server\_principals** catalog view. Each SID is unique for each login in the server.|41|Yes|  
|**NTDomainName**|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**Int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)  
  
  