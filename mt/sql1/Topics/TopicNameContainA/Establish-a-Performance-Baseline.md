---
title: "Establish a Performance Baseline"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Establish a Performance Baseline
To determine whether your [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] system is performing optimally, take performance measurements at regular intervals over time, even when no problems occur, to establish a server performance baseline. Compare each new set of measurements with those taken earlier.  
  
 The following areas affect the performance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]:  
  
-   System resources (hardware)  
  
-   Network architecture  
  
-   The operating system  
  
-   Database applications  
  
-   Client applications  
  
 At a minimum, use baseline measurements to determine:  
  
-   Peak and off-peak hours of operation.  
  
-   Production-query or batch-command response times.  
  
-   Database backup and restore completion times.  
  
 After you establish a server performance baseline, compare the baseline statistics to current server performance. Numbers far above or far below your baseline are candidates for further investigation. They may indicate areas in need of tuning or reconfiguration. For example, if the amount of time to execute a set of queries increases, examine the queries to determine if they can be rewritten, or if column statistics or new indexes must be added.  
  
## See Also  
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)