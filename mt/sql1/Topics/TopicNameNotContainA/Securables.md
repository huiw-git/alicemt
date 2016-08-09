---
title: "Securables"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2015-10-14
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Securables
Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] authorization system regulates access. For example, a table is a securable. Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured. The securable scopes are **server**, **database**, and **schema**.  
  
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
  
-   (Database) Role  
  
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
 The entity that receives permission to a securable is called a principal. The most common principals are logins and database users. Access to securables is controlled by granting or denying permissions, or by adding logins and users to roles which have access. For information about controlling permissions, see [GRANT (Transact-SQL)](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185), [REVOKE (Transact-SQL)](assetId:///9d31d3e7-0883-45cd-bf0e-f0361bbb0956), [DENY (Transact-SQL)](assetId:///c32d1e01-9ee9-4665-a516-fcfece58078e), [sp_addrolemember (Transact-SQL)](assetId:///a583c087-bdb3-46d2-b9e5-3921b3e6d10b), and [sp_droprolemember (Transact-SQL)](assetId:///c2f19ab1-e742-4d56-ba8e-8ffd40cf4925).  
  
> [!CAUTION]  
>  The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation. Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation in an unsupported state.  
  
## Related Content  
 [Getting Started with Database Engine Permissions](../../Topics/TopicNameNotContainA/Getting-Started-with-Database-Engine-Permissions.md)  
  
 [Securing SQL Server](../../Topics/TopicNameNotContainA/Securing-SQL-Server.md)  
  
 [sys.sql_logins (Transact-SQL)](assetId:///8cb239e9-eb8c-4109-9cec-0d35de95fa0e)  
  
 [sys.database_role_members (Transact-SQL)](assetId:///ed1b019d-ca48-4db3-85df-cf6d2db591cf)  
  
 [sys.server_principals (Transact-SQL)](assetId:///c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37)  
  
 [sys.server_role_members (Transact-SQL)](assetId:///efa20414-2c6b-45a2-a7a9-60110a24da18)  
  
 [sys.sql_logins (Transact-SQL)](assetId:///0d9c5b09-86fe-40ff-baab-00b7c051402f)