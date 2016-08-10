---
title: "Audit Schema Object Access Event Class"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c099fa2-c857-4128-aca0-ed8cc3078a43
caps.latest.revision: 30
manager: jhubbard
---
# Audit Schema Object Access Event Class
The **Audit Schema Object Access** event class occurs when an object permission (such as SELECT) is used.  
  
## Audit Schema Object Access Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|**ClientProcessID**|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client provides the client process ID.|9|Yes|  
|**ColumnPermissions**|**int**|Indicates whether a column permission was set. Parse the statement text to determine which permissions were applied. 1=Yes, 0=No.|44|Yes|  
|**DatabaseID**|**int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance. [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] displays the name of the database if the **ServerName** data column is captured in the trace and the server is available. Determine the value for a database by using the DB_ID function.|3|Yes|  
|**DatabaseName**|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|**DBUserName**|**nvarchar**|Issuer's username in the database.|40|Yes|  
|**EventClass**|**int**|Type of event = 114.|27|No|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**HostName**|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the client provides the host name. To determine the host name, use the HOST_NAME function.|8|Yes|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 = system, 0 = user.|60|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login credentials in the form of DOMAIN\username).|11|Yes|  
|**LoginSid**|**image**|Security identification number (SID) of the logged-in user. You can find this information in the **sys.server_principals** catalog view. Each SID is unique for each login in the server.|41|Yes|  
|**NTDomainName**|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|**NTUserName**|**nvarchar**|Windows user name.|6|Yes|  
|**ObjectName**|**nvarchar**|Name of the object whose permissions are being checked.|34|Yes|  
|**ObjectType**|**int**|Value representing the type of the object involved in the event. This value corresponds to the type column in the **sys.objects** catalog view. For values, see [ObjectType Trace Event Column](../../Topics/TopicNameNotContainA/ObjectType-Trace-Event-Column.md).|28|Yes|  
|**OwnerName**|**nvarchar**|Database username of the object owner of the object being targeted.|37|Yes|  
|**ParentName**|**nvarchar**|Name of the schema that the object is within.|59|Yes|  
|**Permissions**|**bigint**|Integer value representing the type of permissions checked.<br /><br /> 1=SELECT ALL<br /><br /> 2=UPDATE ALL<br /><br /> 4=REFERENCES ALL<br /><br /> 8=INSERT<br /><br /> 16=DELETE<br /><br /> 32=EXECUTE (procedures only)|19|Yes|  
|**RequestID**|**int**|ID of the request containing the statement.|49|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**Nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
|**Success**|**int**|1 = success. 0 = failure. For example, a value of 1 indicates success of a permissions check and a value of 0 indicates a failure of that check.|23|Yes|  
|**TextData**|**ntext**|SQL text of the statement.|1|Yes|  
|**TransactionID**|**bigint**|System-assigned ID of the transaction.|4|Yes|  
|**XactSequence**|**bigint**|Token used to describe the current transaction.|50|Yes|  
  
## See Also  
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)