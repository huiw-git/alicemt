---
title: allow updates Server Configuration Option
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
  This option is still present in the **sp\_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The setting has no effect. Direct updates to the system tables are not supported.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../Token\Appliesto/ssNoteDepFutureDontUse_md.md)]  
  
 Changing the **allow updates** option will cause the RECONFIGURE statement to fail. Changes to the **allow updates** option should be removed from all scripts.  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  