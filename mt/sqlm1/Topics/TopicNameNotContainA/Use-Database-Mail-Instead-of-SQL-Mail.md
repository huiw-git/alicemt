---
title: Use Database Mail Instead of SQL Mail
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
---
# Use Database Mail Instead of SQL Mail
  This rule checks the sys.configurations catalog view to determine whether the SQL Mail XPs server\-wide configuration option is set to ON.  
  
## Best Practices Recommendations  
 SQL Mail will be removed in a future version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. To send mail, use Database Mail.  
  
 SQL Mail runs in\-process to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service. If SQL Mail goes down, so does the server. Database Mail runs outside [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in a separate process, is scalable, and does not require Extended MAPI client components to be installed on the production server.  
  
## For More Information  
 [Database Mail](../../Topics\TopicNameNotContainA/Database-Mail.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  