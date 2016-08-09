---
title: "xp_cmdshell Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 17
caps.handback.revision: 0
manager: jhubbard
---
# xp_cmdshell Server Configuration Option
The **xp_cmdshell** option is a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] server configuration option that enables system administrators to control whether the **xp_cmdshell** extended stored procedure can be executed on a system. By default, the **xp_cmdshell** option is disabled on new installations and can be enabled by using the Policy-Based Management or by running the **sp_configure** system stored procedure as shown in the following code example:  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [Administer Servers by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md)