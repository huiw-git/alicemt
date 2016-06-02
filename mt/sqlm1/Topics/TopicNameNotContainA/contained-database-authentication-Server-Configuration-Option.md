---
title: contained database authentication Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
---
# contained database authentication Server Configuration Option
  Use the **contained database authentication** option to enable contained databases on the instance of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
 This server option allows you to control **contained database authentication**.  
  
-   When **contained database authentication** is off \(0\) for the instance, contained databases cannot be created, or attached to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
-   When **contained database authentication** is on \(1\) for the instance, contained databases can be created, or attached to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
 A contained database includes all database settings and metadata required to define the database and has no configuration dependencies on the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] where the database is installed. Users can connect to the database without authenticating a login at the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] level. Isolating the database from the Database Engine makes it possible to easily move the database to another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Including all the database settings in the database enables database owners to manage all the configuration settings for the database. For more information about contained databases, see [Contained Databases](../../Topics\TopicNameNotContainA/Contained-Databases.md).  
  
 If an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has any contained databases the **contained database authentication** setting can be set to 0 by using the **RECONFIGURE WITH OVERRIDE** statement. Setting **contained database authentication** to 0 will disable contained database authentication for the contained databases.  
  
> [!IMPORTANT]  
>  When contained databases are enabled, database users with the ALTER ANY USER permission, such as members of the db\_owner and db\_accessadmin database roles, can grant access to databases and by doing so, grant access to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This means that control over access to the server is no longer limited to members of the sysadmin and securityadmin fixed server role, and logins with the server level CONTROL SERVER and ALTER ANY LOGIN permission. Before allowing contained databases, you should understand the risks associated with contained databases. For more information, see [Security Best Practices with Contained Databases](../../Topics\TopicNameNotContainA/Security-Best-Practices-with-Contained-Databases.md).  
  
## Examples  
 The following example enables contained databases on the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
```tsql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## See Also  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  