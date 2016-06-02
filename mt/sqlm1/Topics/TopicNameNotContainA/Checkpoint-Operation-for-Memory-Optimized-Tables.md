---
title: Checkpoint Operation for Memory-Optimized Tables
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
---
# Checkpoint Operation for Memory-Optimized Tables
  A checkpoint needs to occur periodically for memory\-optimized data in data and delta files to advance the active part of transaction log. The checkpoint allows memory\-optimized tables to restore or recover to the last successful checkpoint and then the active portion of transaction log is applied to update the memory\-optimized tables to complete the recovery. The checkpoint operation for disk\-based tables and memory\-optimized tables are distinct operations. The following describes different scenarios and the checkpoint behavior for disk\-based and memory\-optimized tables:  
  
## Manual Checkpoint  
 When you issue a manual checkpoint, it closes the checkpoint for both disk\-based and memory\-optimized tables. The active data file is closed even though it may be partially filled.  
  
## Automatic Checkpoint  
 Automatic checkpoint is implemented differently for disk\-based and memory\-optimized tables because of the different ways the data is persisted.  
  
 For disk\-based tables, an automatic checkpoint is taken based on the recovery interval configuration option \(for more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../Topic/Change%20the%20Target%20Recovery%20Time%20of%20a%20Database%20\(SQL%20Server\).md)\).  
  
 For memory\-optimized tables, an automatic checkpoint is taken when transaction log file becomes bigger than 1.5 GB since the last checkpoint. This 1.5 GB size  includes transaction log records for both disk\-based and memory\-optimized tables.  
  
## See Also  
 [Creating and Managing Storage for Memory-Optimized Objects](../../Topics\TopicNameNotContainA/Creating-and-Managing-Storage-for-Memory-Optimized-Objects.md)  
  
  