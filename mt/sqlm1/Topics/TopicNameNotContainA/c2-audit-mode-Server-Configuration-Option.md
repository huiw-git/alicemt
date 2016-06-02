---
title: c2 audit mode Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
---
# c2 audit mode Server Configuration Option
  C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or with the **c2 audit mode** option in **sp\_configure**. Selecting this option will configure the server to record both failed and successful attempts to access statements and objects. This information can help you profile system activity and track possible security policy violations.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)] The C2 security standard has been superseded by Common Criteria Certification. See the [common criteria compliance enabled Server Configuration Option](../../Topics\TopicNameNotContainA/common-criteria-compliance-enabled-Server-Configuration-Option.md).  
  
## Audit Log File  
 C2 audit mode data is saved in a file in the default data directory of the instance. If the audit log file reaches its size limit of 200 megabytes \(MB\), [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will create a new file, close the old file, and write all new audit records to the new file. This process will continue until the audit data directory fills up or auditing is turned off. To determine the status of a C2 trace, query the sys.traces catalog view.  
  
> [!IMPORTANT]  
>  C2 audit mode saves a large amount of event information to the log file, which can grow quickly. If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will shut itself down. If auditing is set to start automatically, you must either restart the instance with the **\-f** flag \(which bypasses auditing\), or free up additional disk space for the audit log.  
  
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
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  