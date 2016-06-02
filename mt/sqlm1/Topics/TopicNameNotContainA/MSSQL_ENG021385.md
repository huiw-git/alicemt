---
title: MSSQL_ENG021385
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
---
# MSSQL_ENG021385
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|21385|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Snapshot failed to process publication '%s'. Possibly due to active schema change activity or new articles being added.|  
  
## Explanation  
 This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.  
  
## User Action  
 Restart the Snapshot Agent after changes to the publication database are complete. For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  