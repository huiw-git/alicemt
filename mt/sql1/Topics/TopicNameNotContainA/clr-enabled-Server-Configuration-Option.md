---
title: "clr enabled Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# clr enabled Server Configuration Option
Use the clr enabled option to specify whether user assemblies can be run by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The clr enabled option provides the following values.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Assembly execution not allowed on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|  
|1|Assembly execution allowed on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].|  
  
 WOW64 servers must be restarted before the changes to this setting will take effect. Restart is not required for other server types.  
  
> [!NOTE]  
>  When RECONFIGURE is run and the run value of the clr enabled option is changed from 1 to 0, all application domains containing user assemblies are immediately unloaded.  
  
> [!NOTE]  
>  Common language runtime (CLR) execution is not supported under lightweight pooling. Disable one of two options: "clr enabled" or "lightweight pooling. Features that rely upon CLR and that do not work properly in fiber mode include the **hierarchy** data type, replication, and Policy-Based Management.  
  
## Example  
 The following example first displays the current setting of the clr enabled option and then enables the option by setting the option value to 1. To disable the option, set the value to 0.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## See Also  
 [lightweight pooling Server Configuration Option](../../Topics/TopicNameNotContainA/lightweight-pooling-Server-Configuration-Option.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [lightweight pooling Server Configuration Option](../../Topics/TopicNameNotContainA/lightweight-pooling-Server-Configuration-Option.md)