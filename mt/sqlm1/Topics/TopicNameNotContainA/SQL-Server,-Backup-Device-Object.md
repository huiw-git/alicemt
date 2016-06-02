---
title: SQL Server, Backup Device Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
---
# SQL Server, Backup Device Object
  The **Backup Device** object provides counters to monitor Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup devices used for backup and restore operations. Monitor backup devices when you want to determine the throughput or the progress and performance of your backup and restore operations on a per device basis. To monitor the throughput of the entire database backup or restore operation, use the **Backup\/Restore Throughput\/sec** counter of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **Databases** object. For more information, see [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md).  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **Backup Device** counter.  
  
|SQL Server Backup Device counters|Description|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes\/sec**|Throughput of read and write operations \(in bytes per second\) for a backup device used when backing up or restoring databases. This counter exists only while the backup or restore operation is executing.|  
  
## See Also  
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  