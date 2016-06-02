---
title: Administer Multiple Servers Using Central Management Servers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
---
# Administer Multiple Servers Using Central Management Servers
  You can administer multiple servers by designating Central Management Servers and creating server groups.  
  
## Benefits of Central Management Servers and Server Groups  
 An instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements and Policy\-Based Management policies can be executed at the same time against server groups. You can also view the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] log files on instances that are managed through a Central Management Server. Versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that are earlier than [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] cannot be designated as a Central Management Server.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements can also be executed against local server groups in Registered Servers.  
  
### Related Tasks  
 To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Note that the Central Management Server cannot be a member of a group that it maintains. For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../Topic/Create%20a%20Central%20Management%20Server%20and%20Server%20Group%20\(SQL%20Server%20Management%20Studio\).md).  
  
## See Also  
 [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)  
  
  