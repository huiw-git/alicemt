---
title: "in-doubt xact resolution Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# in-doubt xact resolution Server Configuration Option
Use the **in-doubt xact resolution** option to control the default outcome of transactions that the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Distributed Transaction Coordinator (MS DTC) is unable to resolve. Inability to resolve transactions may be related to the MS DTC down time or an unknown transaction outcome at the time of recovery.  
  
 The following table lists the possible outcome values for resolving an in-doubt transaction.  
  
|Outcome value|Description|  
|-------------------|-----------------|  
|0|No presumption. Recovery fails if MS DTC cannot resolve any in-doubt transactions.|  
|1|Presume commit. Any MS DTC in-doubt transactions are presumed to have committed.|  
|2|Presume abort. Any MS DTC in-doubt transactions are presumed to have aborted.|  
  
 To minimize the possibility of extended down time, an administrator might choose to configure this option either to presume commit or presume abort, as shown in the following example.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -– presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Alternatively, the administrator might want to leave the default (no presumption) and allow recovery to fail in order to be made aware of a DTC failure, as shown in the following example.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -– presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE –- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 –- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 The **in-doubt xact resolution** option is an advanced option. If you are using the **sp_configure** system stored procedure to change the setting, you can change **in-doubt xact resolution** only when **show advanced options** is set to 1. The setting takes effect immediately without a server restart.  
  
> [!NOTE]  
>  Consistent configuration of this option across all [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instances involved in any distributed transactions will help avoid data inconsistencies.  
  
## See Also  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)