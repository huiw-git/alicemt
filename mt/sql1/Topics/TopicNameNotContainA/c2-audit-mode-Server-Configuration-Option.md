---
title: "c2 audit mode Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# c2 audit mode Server Configuration Option
C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or with the **c2 audit mode** option in **sp_configure**. Selecting this option will configure the server to record both failed and successful attempts to access statements and objects. This information can help you profile system activity and track possible security policy violations.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)] The C2 security standard has been superseded by Common Criteria Certification. See the [common criteria compliance enabled Server Configuration Option](../../Topics/TopicNameNotContainA/common-criteria-compliance-enabled-Server-Configuration-Option.md).  
  
## Audit Log File  
 C2 audit mode data is saved in a file in the default data directory of the instance. If the audit log file reaches its size limit of 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] will create a new file, close the old file, and write all new audit records to the new file. This process will continue until the audit data directory fills up or auditing is turned off. To determine the status of a C2 trace, query the sys.traces catalog view.  
  
> [!IMPORTANT]  
>  C2 audit mode saves a large amount of event information to the log file, which can grow quickly. If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] will shut itself down. If auditing is set to start automatically, you must either restart the instance with the **-f** flag (which bypasses auditing), or free up additional disk space for the audit log.  
  
## Permissions  
 Requires membership in the **sysadmin** fixed server role.  
  
## Example  
 The following example turns on C2 audit mode.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## See Also  
 [sp_configure (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)