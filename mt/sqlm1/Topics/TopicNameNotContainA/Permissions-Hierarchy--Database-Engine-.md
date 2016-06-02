---
title: Permissions Hierarchy (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
---
# Permissions Hierarchy (Database Engine)
  The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] manages a hierarchical collection of entities that can be secured with permissions. These entities are known as *securables*. The most prominent securables are servers and databases, but discrete permissions can be set at a much finer level. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] regulates the actions of principals on securables by verifying that they have been granted appropriate permissions.  
  
 The following illustration shows the relationships among the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] permissions hierarchies.  
  
 The permissions system works the same in all versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)], [!INCLUDE[ssDW](../../Token\Other/ssDW_md.md)], [!INCLUDE[ssAPS](../../Token\Other/ssAPS_md.md)], however some features are not available in all versions. For example, server\-level permission cannot be configured in Azure products.  
  
 ![Diagram of Database Engine permissions hierarchies](../../Images\Image\ImageNotContaina/wj_security_layers.gif "wj_security_layers")  
  
## Chart of SQL Server Permissions  
 For a poster sized chart of all [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] permissions in pdf format, see [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## Working with Permissions  
 Permissions can be manipulated with the familiar [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries GRANT, DENY, and REVOKE. Information about permissions is visible in the [sys.server\_permissions](../Topic/sys.server_permissions%20\(Transact-SQL\).md) and [sys.database\_permissions](../Topic/sys.database_permissions%20\(Transact-SQL\).md) catalog views. There is also support for querying permissions information by using built\-in functions.  
  
 For information about designing a permissions system, see [Getting Started with Database Engine Permissions](../../Topics\TopicNameNotContainA/Getting-Started-with-Database-Engine-Permissions.md).  
  
## See Also  
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)   
 [Permissions &#40;Database Engine&#41;](../Topic/Permissions%20\(Database%20Engine\).md)   
 [Securables](../../Topics\TopicNameNotContainA/Securables.md)   
 [Principals &#40;Database Engine&#41;](../Topic/Principals%20\(Database%20Engine\).md)   
 [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md)   
 [REVOKE &#40;Transact-SQL&#41;](../Topic/REVOKE%20\(Transact-SQL\).md)   
 [DENY &#40;Transact-SQL&#41;](../Topic/DENY%20\(Transact-SQL\).md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../Topic/HAS_PERMS_BY_NAME%20\(Transact-SQL\).md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../Topic/sys.fn_builtin_permissions%20\(Transact-SQL\).md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../Topic/sys.server_permissions%20\(Transact-SQL\).md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../Topic/sys.database_permissions%20\(Transact-SQL\).md)  
  
  