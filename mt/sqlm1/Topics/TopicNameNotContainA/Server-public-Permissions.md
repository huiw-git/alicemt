---
title: Server public Permissions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
---
# Server public Permissions
  This rule determines whether the public server role has server permissions. Every login that is created on the server is a member of the public server role. If this condition is met, every login on the server will have server permissions.  
  
## Best Practices Recommendations  
 Do not grant server permissions to the server public role.  
  
> [!IMPORTANT]  
>  After setup completes the **PUBLIC** role has **CONNECT** permission on all the endpoints except the **Dedicated Admin Connection**. This is normal and should not be normally changed. \(Access is controlled by using the **CONNECT SQL** permission which is automatically granted when new logins are created.\)  
  
### For more information  
 [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md)  
  
  