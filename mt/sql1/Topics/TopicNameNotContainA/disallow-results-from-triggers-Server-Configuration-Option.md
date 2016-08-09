---
title: "disallow results from triggers Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# disallow results from triggers Server Configuration Option
Use the **disallow results from triggers** option to control whether triggers return result sets. Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../Topics/TopicNameNotContainA/tokens/ssNoteDepNextDontUse_md.md)] We recommend that you set this value to 1.  
  
 When set to 1, the **disallow results from triggers** option is set to ON. The default setting for this option is 0 (OFF). If this option is set to 1 (ON), any attempt by a trigger to return a result set fails, and the user receives the following error message:  
  
 "Msg 524, Level 16, State 1, Procedure <Procedure Name\>, Line <Line#>  
  
 "A trigger returned a resultset and the server option 'disallow_results_from_triggers' is true."  
  
 The **disallow results from triggers** option is applied at the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance level, and it will determine behavior for all existing triggers within the instance.  
  
 The **disallow results from triggers** option is an advanced option. If you are using the **sp_configure** system stored procedure to change the setting, you can change disallow results from triggers only when **show advanced options** is set to 1. The setting takes effect immediately without a server restart.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)