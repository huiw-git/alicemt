---
title: Guest Permissions on User Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
---
# Guest Permissions on User Databases
  This rule determines whether the guest user has permission to access the database. This rule applies to user databases only.  
  
## Best Practices Recommendations  
 Revoke the guest user permission to access the database if it is not required.  
  
 The guest user cannot be dropped, but guest user can be disabled by revoking its CONNECT permission by executing REVOKE CONNECT FROM GUEST within any database other than master, tempdb, or msdb.  
  
## For More Information  
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  