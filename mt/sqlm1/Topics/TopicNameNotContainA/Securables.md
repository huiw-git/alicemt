---
title: Securables
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
---
# Securables
  Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] authorization system regulates access. For example, a table is a securable. Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured. The securable scopes are **server**, **database**, and **schema**.  
  
## Securable scope: Server  
 The **server** securable scope contains the following securables:  
  
-   Availability group  
  
-   Endpoint  
  
-   Login  
  
-   Server role  
  
-   Database  
  
## Securable scope: Database  
 The **database** securable scope contains the following securables:  
  
-   Application role  
  
-   Assembly  
  
-   Asymmetric key  
  
-   Certificate  
  
-   Contract  
  
-   Fulltext catalog  
  
-   Fulltext stoplist  
  
-   Message type  
  
-   Remote Service Binding  
  
-   \(Database\) Role  
  
-   Route  
  
-   Schema  
  
-   Search property list  
  
-   Service  
  
-   Symmetric key  
  
-   User  
  
## Securable scope: Schema  
 The **schema** securable scope contains the following securables:  
  
-   Type  
  
-   XML schema collection  
  
-   Object – The object class has the following members:  
  
    -   Aggregate  
  
    -   Function  
  
    -   Procedure  
  
    -   Queue  
  
    -   Synonym  
  
    -   Table  
  
    -   View  
  
## Controlling Access to a Securable  
 The entity that receives permission to a securable is called a principal. The most common principals are logins and database users. Access to securables is controlled by granting or denying permissions, or by adding logins and users to roles which have access. For information about controlling permissions, see [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md), [REVOKE &#40;Transact-SQL&#41;](../Topic/REVOKE%20\(Transact-SQL\).md), [DENY &#40;Transact-SQL&#41;](../Topic/DENY%20\(Transact-SQL\).md), [sp_addrolemember &#40;Transact-SQL&#41;](../Topic/sp_addrolemember%20\(Transact-SQL\).md), and [sp_droprolemember &#40;Transact-SQL&#41;](../Topic/sp_droprolemember%20\(Transact-SQL\).md).  
  
> [!CAUTION]  
>  The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation. Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation in an unsupported state.  
  
## Related Content  
 [Getting Started with Database Engine Permissions](../../Topics\TopicNameNotContainA/Getting-Started-with-Database-Engine-Permissions.md)  
  
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)  
  
 [sys.database_principals &#40;Transact-SQL&#41;](../Topic/sys.database_principals%20\(Transact-SQL\).md)  
  
 [sys.database_role_members &#40;Transact-SQL&#41;](../Topic/sys.database_role_members%20\(Transact-SQL\).md)  
  
 [sys.server_principals &#40;Transact-SQL&#41;](../Topic/sys.server_principals%20\(Transact-SQL\).md)  
  
 [sys.server_role_members &#40;Transact-SQL&#41;](../Topic/sys.server_role_members%20\(Transact-SQL\).md)  
  
 [sys.sql_logins &#40;Transact-SQL&#41;](../Topic/sys.sql_logins%20\(Transact-SQL\).md)  
  
  