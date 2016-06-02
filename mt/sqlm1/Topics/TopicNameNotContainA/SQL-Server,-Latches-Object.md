---
title: SQL Server, Latches Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
---
# SQL Server, Latches Object
  The **SQLServer:Latches** object in Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides counters to monitor internal [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource locks called latches. Monitoring the latches to determine user activity and resource usage can help you to identify performance bottlenecks.  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **Latches** counters.  
  
|SQL Server Latches counters|Description|  
|---------------------------------|-----------------|  
|**Average Latch Wait Time \(ms\)**|Average latch wait time \(in milliseconds\) for latch requests that had to wait.|  
|**Latch Waits\/sec**|Number of latch requests that could not be granted immediately.|  
|**Number of SuperLatches**|Number of latches that are currently SuperLatches.|  
|**SuperLatch Demotions\/sec**|Number of SuperLatches that have been demoted to regular latches in the last second.|  
|**SuperLatch Promotions\/sec**|Number of latches that have been promoted to SuperLatches in the last second.|  
|**Total Latch Wait Time \(ms\)**|Total latch wait time \(in milliseconds\) for latch requests in the last second.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  