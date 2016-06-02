---
title: affinity64 mask Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
---
# affinity64 mask Server Configuration Option
  The affinity64 mask binds processors to specific threads, similar to the affinity mask option. Use affinity mask to bind the first 32 processors, and use affinity64 mask to bind the remaining processors on the computer. This option is only visible on the 64\-bit version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../Token\Other/ssNoteDepNextAvoid_md.md)] Use [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md) instead.  
  
## See Also  
 [affinity mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  