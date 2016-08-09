---
title: "affinity64 mask Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# affinity64 mask Server Configuration Option
The affinity64 mask binds processors to specific threads, similar to the affinity mask option. Use affinity mask to bind the first 32 processors, and use affinity64 mask to bind the remaining processors on the computer. This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../Topics/TopicNameNotContainA/tokens/ssNoteDepNextAvoid_md.md)] Use [ALTER SERVER CONFIGURATION SET PROCESS AFFINITY (Transact-SQL)](assetId:///f3059e42-5f6f-4a64-903c-86dca212a4b4) instead.  
  
## See Also  
 [affinity mask Server Configuration Option](../../Topics/TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)