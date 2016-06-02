---
title: Back Up and Restore of System Databases (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aef0c4fa-ba67-413d-9359-1a67682fdaab
---
# Back Up and Restore of System Databases (SQL Server)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] maintains a set of system\-level databases, s*ystem databases*, which are essential for the operation of a server instance. Several of the system databases must be backed up after every significant update. The system databases that you must always back up include **msdb**, **master**, and **model**. If any database uses replication on the server instance, there is a **distribution** system database that you must also back up. Backups of these system databases let you restore and recover the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system in the event of system failure, such as the loss of a hard disk.  
  
 The following table summarizes all of the system databases.  
  
|System database|Description|Are backups required?|Recovery model|Comments|  
|---------------------|-----------------|---------------------------|--------------------|--------------|  
|[master](../../Topics\TopicNameNotContainA/master-Database.md)|The database that records all of the system level information for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system.|Yes|Simple|Back up **master** as often as necessary to protect the data sufficiently for your business needs. We recommend a regular backup schedule, which you can supplement with an additional backup after a substantial update.|  
|[model](../../Topics\TopicNameNotContainA/model-Database.md)|The template for all databases that are created on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|Yes|User configurable\*|Back up **model** only when necessary for your business needs; for example, immediately after customizing its database options.<br /><br /> **Best practice:** We recommend that you create only full database backups of **model**, as required. Because **model** is small and rarely changes, backing up the log is unnecessary.|  
|[msdb](../../Topics\TopicNameNotContainA/msdb-Database.md)|The database used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent for scheduling alerts and jobs, and for recording operators. **msdb** also contains history tables such as the backup and restore history tables.|Yes|Simple \(default\)|Back up **msdb** whenever it is updated.|  
|[Resource](../../Topics\TopicNameNotContainA/Resource-Database.md) \(RDB\)|A read\-only database that contains copies of all system objects that ship with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|No|—|The **Resource** database resides in the mssqlsystemresource.mdf file, which contains only code. Therefore, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot back up the **Resource** database.<br /><br /> Note: You can perform a file\-based or a disk\-based backup on the mssqlsystemresource.mdf file by treating the file as if it were a binary \(.exe\) file, instead of a database file. But you cannot use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] restore on the backups. Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current **Resource** database with an out\-of\-date or potentially insecure version.|  
|[tempdb](../../Topics\TopicNameNotContainA/tempdb-Database.md)|A workspace for holding temporary or intermediate result sets. This database is re\-created every time an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started. When the server instance is shut down, any data in **tempdb** is deleted permanently.|No|Simple|You cannot back up the **tempdb** system database.|  
|[Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)|A database that exists only if the server is configured as a replication Distributor. This database stores metadata and history data for all types of replication, and transactions for transactional replication.|Yes|Simple|For information about when to back up the **distribution** database, see [Back Up and Restore Replicated Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md).|  
  
 \*To learn the current recovery model of the model, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md) or [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md).  
  
## Limitations on Restoring System Databases  
  
-   System databases can be restored only from backups that are created on the version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that the server instance is currently running. For example, to restore a system database on a server instance that is running on [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1, you must use a database backup that was created after the server instance was upgraded to [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1.  
  
-   To restore any database, the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be running. Startup of an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] requires that the **master** database is accessible and at least partly usable. If **master** becomes unusable, you can return the database to a usable state in either of the following ways:  
  
    -   Restore **master** from a current database backup.  
  
         If you can start the server instance, you should be able to restore **master** from a full database backup.  
  
    -   Rebuild **master** completely.  
  
         If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you must rebuild **master**. For more information, see [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md).  
  
        > [!IMPORTANT]  
        >  Rebuilding **master** rebuilds all of the system databases.  
  
-   Under some circumstances, problems recovering the model database may require rebuilding the system databases or replacing the mdf and ldf files for the model database. For more information, see [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)  
  
-   [Restore the master Database &#40;Transact-SQL&#41;](../Topic/Restore%20the%20master%20Database%20\(Transact-SQL\).md)  
  
-   [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md)  
  
-   [Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md)  
  
## See Also  
 [Distribution Database](../../Topics\TopicNameNotContainA/Distribution-Database.md)   
 [master Database](../../Topics\TopicNameNotContainA/master-Database.md)   
 [msdb Database](../../Topics\TopicNameNotContainA/msdb-Database.md)   
 [model Database](../../Topics\TopicNameNotContainA/model-Database.md)   
 [Resource Database](../../Topics\TopicNameNotContainA/Resource-Database.md)   
 [tempdb Database](../../Topics\TopicNameNotContainA/tempdb-Database.md)  
  
  