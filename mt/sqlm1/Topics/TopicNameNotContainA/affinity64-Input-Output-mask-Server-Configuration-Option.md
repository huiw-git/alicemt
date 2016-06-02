---
title: affinity64 Input-Output mask Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
---
# affinity64 Input-Output mask Server Configuration Option
  The **affinity64 I\/O mask** binds [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] disk I\/O to a specified subset of CPUs, similar to the **affinity I\/O mask** option. Use **affinity I\/O mask** to bind the first 32 processors, and use **affinity64 I\/O mask** to bind the remaining processors on the computer. If you reconfigure the **affinity64 I\/O mask**, you must restart the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This option is only visible on the 64\-bit version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## See Also  
 [affinity Input-Output mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-Input-Output-mask-Server-Configuration-Option.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  