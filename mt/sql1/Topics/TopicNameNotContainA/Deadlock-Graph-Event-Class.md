---
title: "Deadlock Graph Event Class"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
caps.latest.revision: 32
manager: jhubbard
---
# Deadlock Graph Event Class
The **Deadlock Graph** event class provides an XML description of a deadlock. This class occurs simultaneously with the **Lock:Deadlock** event class.  
  
## Deadlock Graph Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Type of event = 148.|27|No|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 = system, 0 = user. This value is always 1 for this event.|60|Yes|  
|**LoginName**|**nvarchar**|Name of the login of the user (either the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login credentials in the form of DOMAIN\username). This value is always the system user for this event.|11|Yes|  
|**LoginSid**|**image**|Security identification number (SID) of the logged-in user. You can find this information in the sys.server_principals catalog view. Each SID is unique for each login in the server. This value is always the SID of the system user for this event.|41|Yes|  
|**ServerName**|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] being traced.|26|No|  
|**SessionLoginName**|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the deadlock was detected.|14|Yes|  
|**TextData**|**ntext**|XML description of the deadlock.|1|Yes|  
|**TransactionID**|**bigint**|Not used.|4|Yes|  
  
## See Also  
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [Lock:Deadlock Event Class](../Topic/Lock:Deadlock%20Event%20Class.md)