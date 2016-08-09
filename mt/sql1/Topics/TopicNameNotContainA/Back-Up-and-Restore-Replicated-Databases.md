---
title: "Back Up and Restore Replicated Databases"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
caps.latest.revision: 41
manager: jhubbard
---
# Back Up and Restore Replicated Databases
Replicated databases require special attention with regards to backing up and restoring data. This topic provides introductory information and links to further information on backup and restore strategies for each type of replication.  
  
 Replication supports restoring replicated databases to the same server and database from which the backup was created. If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved. In this case, you must recreate all publications and subscriptions after backups are restored.  
  
> [!NOTE]  
>  It is possible to restore a replicated database to a standby server if log shipping is being used. For more information, see [Log Shipping and Replication (SQL Server)](../../Topics/TopicNameNotContainA/Log-Shipping-and-Replication--SQL-Server-.md).  
  
 Replicated databases and their associated system databases should be backed up regularly. Back up the following databases:  
  
-   The publication database at the Publisher  
  
-   The distribution database at the Distributor  
  
-   The subscription database at each Subscriber  
  
-   The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers. These databases should be backed up at the same time as each other and the relevant replication database. For example, back up the **master** and **msdb** databases at the Publisher at the same time you back up the publication database. If the publication database is restored, ensure that the **master** and **msdb** database are consistent with the publication database in terms of replication configuration and settings.  
  
 If you perform regular log backups, any replication-related changes should be captured in the log backups. If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed. For more information, see [Common Actions Requiring an Updated Backup](../../Topics/TopicNameNotContainA/Common-Actions-Requiring-an-Updated-Backup.md).  
  
## Backup and Restore Strategies  
 The strategies for backing up and restoring each node in a replication topology differ according to the type of replication used. For information on backup and restore strategies for each type of replication, see the following topics:  
  
-   [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../../Topics/TopicNameNotContainA/Strategies-for-Backing-Up-and-Restoring-Snapshot-and-Transactional-Replication.md)  
  
-   [Strategies for Backing Up and Restoring Merge Replication](../../Topics/TopicNameNotContainA/Strategies-for-Backing-Up-and-Restoring-Merge-Replication.md)  
  
 As part of any recovery strategy, always keep a current script of your replication settings in a safe location. In the event of server failure or the need to set up a test environment, you can modify the script by changing server name references, and it can be used to help recreate your replication settings. In addition to scripting your current replication settings, you should script the enabling and disabling of replication. For information about scripting replication objects, see [Scripting Replication](../../Topics/TopicNameNotContainA/Scripting-Replication.md).  
  
## See Also  
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Best Practices for Replication Administration](../../Topics/TopicNameNotContainA/Best-Practices-for-Replication-Administration.md)