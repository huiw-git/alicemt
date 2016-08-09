---
title: "Start Data Movement on an Always On Secondary Database (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
caps.latest.revision: 18
caps.handback.revision: 0
manager: jhubbard
---
# Start Data Movement on an Always On Secondary Database (SQL Server)
This topic contains information about how to start data synchronization after you add a database to an Always On availability group. For each new primary replica, secondary databases must be prepared on the server instances that host the secondary replicas. Then each of these secondary databases must be manually joined to the availability group.  
  
> [!NOTE]  
>  If the file paths are identical on every server instance that hosts an availability replica for an availability group, the [New Availability Group Wizard](../../Topics/TopicNameNotContainA/Use-the-Availability-Group-Wizard--SQL-Server-Management-Studio-.md), [Add Replica to Availability Group Wizard](../../Topics/TopicNameNotContainA/Use-the-Add-Replica-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md), or [Add Database to Availability Group Wizard](../../Topics/TopicNameNotContainA/Use-the-Add-Database-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md) might be able to automatically start data synchronization for you.  
  
 To start data synchronization manually, you need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:  
  
1.  Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY). You can use either of the following alternative approaches:  
  
    -   Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY. Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.  
  
         **For more information:**  
  
         [Manually Prepare a Secondary Database for an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Manually-Prepare-a-Secondary-Database-for-an-Availability-Group--SQL-Server-.md)  
  
    -   If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to Always On Availability Groups. Migrating a log shipping secondary database requires that it use the same database name as the primary database and that it reside on a server instance that is hosting a secondary replica for the availability group. Furthermore, the availability group must be configured so that the primary replica is preferred for backups and is a candidate for performing backups (that is, that has a backup priority that is >0). Once the backup job has run on the primary database, you will need to disable the backup job, and once the restore job has run on a given secondary database, you will need to disable the restore job.  
  
        > [!NOTE]  
        >  After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.  
  
         **For more information:**  
  
         [Prerequisites for Migrating from Log Shipping to Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Prerequisites-for-Migrating-from-Log-Shipping-to-Always-On-Availability-Groups--SQL-Server-.md)  
  
         [Configure Backup on Availability Replicas (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Backup-on-Availability-Replicas--SQL-Server-.md)  
  
2.  As soon as possible, join each newly prepared secondary database to the availability group.  
  
     **For more information:**  
  
     [Join a Secondary Database to an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Join-a-Secondary-Database-to-an-Availability-Group--SQL-Server-.md)  
  
##  <a name="LaunchWiz"></a> Related Tasks  
  
-   [Use the New Availability Group Dialog Box (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-New-Availability-Group-Dialog-Box--SQL-Server-Management-Studio-.md)  
  
-   [Use the Add Replica to Availability Group Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Add-Replica-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
-   [Use the Add Database to Availability Group Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Add-Database-to-Availability-Group-Wizard--SQL-Server-Management-Studio-.md)  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)