---
title: allow updates Server Configuration Option
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
---
# allow updates Server Configuration Option
  This option is still present in the **sp_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. The setting has no effect. Direct updates to the system tables are not supported.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../Topics/TopicNameContainA/includes/ssNoteDepFutureDontUse_md.md)]  
  
 Changing the **allow updates** option will cause the RECONFIGURE statement to fail. Changes to the **allow updates** option should be removed from all scripts.  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)  
  
  