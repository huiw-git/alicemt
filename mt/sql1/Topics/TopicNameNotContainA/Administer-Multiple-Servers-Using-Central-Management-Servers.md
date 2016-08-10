---
title: "Administer Multiple Servers Using Central Management Servers"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Administer Multiple Servers Using Central Management Servers
You can administer multiple servers by designating Central Management Servers and creating server groups.  
  
## Benefits of Central Management Servers and Server Groups  
 An instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements and Policy-Based Management policies can be executed at the same time against server groups. You can also view the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] log files on instances that are managed through a Central Management Server. Versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that are earlier than [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] cannot be designated as a Central Management Server.  
  
 [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements can also be executed against local server groups in Registered Servers.  
  
### Related Tasks  
 To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. Note that the Central Management Server cannot be a member of a group that it maintains. For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group (SQL Server Management Studio)](../../Topics/TopicNameContainA/Create-a-Central-Management-Server-and-Server-Group--SQL-Server-Management-Studio-.md).  
  
## See Also  
 [Administer Servers by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)