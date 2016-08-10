---
title: "MSSQL_ENG021385"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG021385
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21385|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Snapshot failed to process publication '%s'. Possibly due to active schema change activity or new articles being added.|  
  
## Explanation  
 This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.  
  
## User Action  
 Restart the Snapshot Agent after changes to the publication database are complete. For more information, see [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md) and [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)