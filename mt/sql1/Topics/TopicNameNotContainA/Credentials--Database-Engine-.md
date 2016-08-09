---
title: "Credentials (Database Engine)"
ms.custom: na
ms.date: 2015-08-19
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Credentials (Database Engine)
A credential is a record that contains the authentication information (credentials) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This information is used internally by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Most credentials contain a Windows user name and password.  
  
 The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by way of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication to access resources outside the server instance. When the external resource is Windows, the user is authenticated as the Windows user specified in the credential. A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins. However, a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login can be mapped to only one credential.  
  
 For credentials that are stored in the master database and can be used throughout the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d). For credentials used by a specific database, and portable with that database, see [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).  
  
 System credentials are created automatically and are associated with specific endpoints. Names for system credentials start with two hash signs (##).  
  
 For more information about credentials, see the [sys.credentials](assetId:///ea48cf80-904a-4273-a950-6d35b1b0a1b6) and [sys.database_credentials (Transact-SQL)](assetId:///796322df-e62a-45bf-b519-89e1d521abce) catalog views.  
  
## Related Content  
 [Create a Credential](../../Topics/TopicNameContainA/Create-a-Credential.md) [CREATE CREDENTIAL (Transact-SQL))](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d) [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045)  
  
 [Securing SQL Server](../../Topics/TopicNameNotContainA/Securing-SQL-Server.md)