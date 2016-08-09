---
title: "SQL Server Login Password Expiration"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Login Password Expiration
This rule checks whether "Password expiration" of each [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login is enabled. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../Topics/TopicNameContainA/tokens/winxpsvr_md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login password.  
  
## Best Practices Recommendations  
 We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../Topics/TopicNameContainA/tokens/winxpsvr_md.md)].  
  
 If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication is not required in your environment, use Windows Authentication. For more information, see [Choose an Authentication Mode](../../Topics/TopicNameNotContainA/Choose-an-Authentication-Mode.md).  
  
 Enable "Password expiration" for all the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins. Use [ALTER LOGIN](assetId:///e247b84e-c99e-4af8-8b50-57586e1cb1c5) to configure the password policy for the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login.  
  
## For More Information  
 [Password Policy](../../Topics/TopicNameNotContainA/Password-Policy.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)