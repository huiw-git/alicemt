---
title: Credentials (Database Engine)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
---
# Credentials (Database Engine)
  A credential is a record that contains the authentication information \(credentials\) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This information is used internally by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Most credentials contain a Windows user name and password.  
  
 The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by way of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to access resources outside the server instance. When the external resource is Windows, the user is authenticated as the Windows user specified in the credential. A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins. However, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login can be mapped to only one credential.  
  
 For credentials that are stored in the master database and can be used throughout the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md). For credentials used by a specific database, and portable with that database, see [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20SCOPED%20CREDENTIAL%20\(Transact-SQL\).md).  
  
 System credentials are created automatically and are associated with specific endpoints. Names for system credentials start with two hash signs \(\#\#\).  
  
 For more information about credentials, see the [sys.credentials](../Topic/sys.credentials%20\(Transact-SQL\).md) and [sys.database_credentials &#40;Transact-SQL&#41;](../Topic/sys.database_credentials%20\(Transact-SQL\).md) catalog views.  
  
## Related Content  
 [Create a Credential](../../Topics\TopicNameContainA/Create-a-Credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md) [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20SCOPED%20CREDENTIAL%20\(Transact-SQL\).md)  
  
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)  
  
  