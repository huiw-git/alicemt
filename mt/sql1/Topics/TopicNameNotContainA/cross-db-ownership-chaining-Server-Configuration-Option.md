---
title: "cross db ownership chaining Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# cross db ownership chaining Server Configuration Option
Use the **cross db ownership chaining** option to configure cross-database ownership chaining for an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 This server option allows you to control cross-database ownership chaining at the database level or to allow cross-database ownership chaining for all databases:  
  
-   When **cross db ownership chaining** is off (0) for the instance, cross-database ownership chaining is disabled for all databases.  
  
-   When **cross db ownership chaining** is on (1) for the instance, cross-database ownership chaining is on for all databases.  
  
-   You can set cross-database ownership chaining for individual databases using the SET clause of the ALTER DATABASE statement. If you are creating a new database, you can set the cross-database ownership chaining option for the new database using the CREATE DATABASE statement.  
  
     Setting **cross db ownership chaining** to 1 is not recommended unless all of the databases hosted by the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] must participate in cross-database ownership chaining and you are aware of the security implications of this setting.  
  
## Controlling Cross-Database Ownership Chaining  
 Before turning cross-database ownership chaining on or off, consider the following:  
  
-   You must be a member of the **sysadmin** fixed server role to turn cross-database ownership chaining on or off.  
  
-   Before turning off cross-database ownership chaining on a production server, fully test all applications, including third-party applications, to ensure that the changes do not affect application functionality.  
  
-   You can change the **cross db ownership chaining** option while the server is running if you specify RECONFIGURE with **sp_configure**.  
  
-   If you have databases that require cross-database ownership chaining, the recommended practice is to turn off the **cross db ownership chaining** option for the instance using **sp_configure**; then turn on cross-database ownership chaining for individual databases that require it using the ALTER DATABASE statement.  
  
## See Also  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)