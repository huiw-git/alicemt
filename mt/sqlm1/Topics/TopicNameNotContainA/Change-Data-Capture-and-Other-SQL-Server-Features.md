---
title: Change Data Capture and Other SQL Server Features
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
---
# Change Data Capture and Other SQL Server Features
  This topic describes how the following features interact with change data capture:  
  
-   [Change tracking](#ChangeTracking)  
  
-   [Database mirroring](#DatabaseMirroring)  
  
-   [Transactional replication](#TransReplication)  
  
-   [Restoring or Attaching a Database Enabled for Change Data Capture](#RestoreOrAttach)  
  
##  <a name="ChangeTracking"></a> Change Tracking  
 Change data capture and [change tracking](../Topic/About%20Change%20Tracking%20\(SQL%20Server\).md) can be enabled on the same database. No special considerations are required. For more information, see [Work with Change Tracking &#40;SQL Server&#41;](../Topic/Work%20with%20Change%20Tracking%20\(SQL%20Server\).md).  
  
##  <a name="DatabaseMirroring"></a> Database Mirroring  
 A database that is enabled for change data capture can be mirrored. To ensure that capture and cleanup happen automatically after a failover, follow these steps:  
  
1.  Ensure that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent is running on the new principal server instance.  
  
2.  Create the capture job and cleanup job on the new principal database \(the former mirror database\). To create the jobs, use the [sp\_cdc\_add\_job](../Topic/sys.sp_cdc_add_job%20\(Transact-SQL\).md) stored procedure.  
  
 To view the current configuration of a cleanup or capture job, use the [sys.sp\_cdc\_help\_jobs](../Topic/sys.sp_cdc_help_jobs%20\(Transact-SQL\).md) stored procedure on the new principal server instance. For a given database, the capture job is named cdc.*database\_name*\_capture, and the cleanup job is named cdc.*database\_name*\_cleanup, where *database\_name* is the name of the database.  
  
 To change the configuration of a job, use the [sys.sp\_cdc\_change\_job](../Topic/sys.sp_cdc_change_job%20\(Transact-SQL\).md) stored procedure.  
  
 For information about database mirroring, see [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md).  
  
##  <a name="TransReplication"></a> Transactional Replication  
 Change data capture and transactional replication can coexist in the same database, but population of the change tables is handled differently when both features are enabled. Change data capture and transactional replication always use the same procedure, [sp\_replcmds](../Topic/sp_replcmds%20\(Transact-SQL\).md), to read changes from the transaction log. When change data capture is enabled on its own, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job calls **sp\_replcmds**. When both features are enabled on the same database, the Log Reader Agent calls **sp\_replcmds**. This agent populates both the change tables and the distribution database tables. For more information, see [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md).  
  
 Consider a scenario in which change data capture is enabled on the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database, and two tables are enabled for capture. To populate the change tables, the capture job calls **sp\_replcmds**. The database is enabled for transactional replication, and a publication is created. Now, the Log Reader Agent is created for the database and the capture job is deleted. The Log Reader Agent continues to scan the log from the last log sequence number that was committed to the change table. This ensures data consistency in the change tables. If transactional replication is disabled in this database, the Log Reader Agent is removed and the capture job is re\-created.  
  
> [!NOTE]  
>  When the Log Reader Agent is used for both change data capture and transactional replication, replicated changes are first written to the distribution database. Then, captured changes are written to the change tables. Both operations are committed together. If there is any latency in writing to the distribution database, there will be a corresponding latency before changes appear in the change tables.  
  
 The **proc exec** option of transactional replication is not available when change data capture is enabled.  
  
##  <a name="RestoreOrAttach"></a> Restoring or Attaching a Database Enabled for Change Data Capture  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the following logic to determine if change data capture remains enabled after a database is restored or attached:  
  
-   If a database is restored to the same server with the same database name, change data capture remains enabled.  
  
-   If a database is restored to another server, by default change data capture is disabled and all related metadata is deleted.  
  
     To retain change data capture, use the **KEEP\_CDC** option when restoring the database. For more information about this option, see [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md).  
  
-   If a database is detached and attached to the same server or another server, change data capture remains enabled.  
  
-   If a database is attached or restored with the **KEEP\_CDC** option to any edition other than Enterprise, the operation is blocked because change data capture requires [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise. Error message 934 is displayed:  
  
     `SQL Server cannot load database '%.*ls' because Change Data Capture is enabled. The currently installed edition of SQL Server does not support Change Data Capture. Either restore database without KEEP_CDC option, or upgrade the instance to one that supports Change Data Capture.`  
  
 You can use [sys.sp\_cdc\_disable\_db](../Topic/sys.sp_cdc_disable_db%20\(Transact-SQL\).md) to remove change data capture from a restored or attached database.  
  
## Change Data Capture and Always On  
 When you use Always On, change enumeration should be done on the Secondary replication to reduce the disk load on the primary.  
  
## See Also  
 [Administer and Monitor Change Data Capture &#40;SQL Server&#41;](../Topic/Administer%20and%20Monitor%20Change%20Data%20Capture%20\(SQL%20Server\).md)  
  
  