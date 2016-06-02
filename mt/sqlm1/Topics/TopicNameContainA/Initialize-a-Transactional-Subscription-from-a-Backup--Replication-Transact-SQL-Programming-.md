---
title: Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
---
# Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)
  Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
### To initialize a transactional subscriber from a backup  
  
1.  For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication &#40;Transact-SQL&#41;](../Topic/sp_helppublication%20\(Transact-SQL\).md) at the Publisher on the publication database. Note the value of **allow\_initialize\_from\_backup** in the result set.  
  
    -   If the value is **1**, the publication supports this functionality.  
  
    -   If the value is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](../Topic/sp_changepublication%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **allow\_initialize\_from\_backup** for **@property** and a value of **true** for **@value**.  
  
2.  For a new publication, execute [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **true** for **allow\_initialize\_from\_backup**. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
    > [!WARNING]  
    >  To avoid missing subscriber data, when using **sp\_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.  
  
3.  Create a backup of the publication database using the [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md) statement.  
  
4.  Restore the backup on the Subscriber using the [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md) statement.  
  
5.  At the Publisher on the publication database, execute the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](../Topic/sp_addsubscription%20\(Transact-SQL\).md). Specify the following parameters:  
  
    -   **@sync\_type** \- a value of **initialize with backup**.  
  
    -   **@backupdevicetype** \- the type of backup device: **logical** \(default\), **disk**, or **tape**.  
  
    -   **@backupdevicename** \- the logical or physical backup device to use for the restore.  
  
         For a logical device, specify the name of the backup device specified when **sp\_addumpdevice** was used to create the device.  
  
         For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.  
  
    -   \(Optional\) **@password** \- a password that was provided when the backup set was created.  
  
    -   \(Optional\) **@mediapassword** \- a password that was provided when the media set was formatted.  
  
    -   \(Optional\) **@fileidhint** \- identifier for the backup set to be restored. For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.  
  
    -   \(Optional for tape devices\) **@unload** \- specify a value of **1** \(default\) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.  
  
6.  \(Optional\) For a pull subscription, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription%20\(Transact-SQL\).md) and [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md) at the Subscriber on the subscription database. For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
7.  \(Optional\) Start the Distribution Agent. For more information, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md) or [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
## See Also  
 [Copy Databases with Backup and Restore](../../Topics\TopicNameNotContainA/Copy-Databases-with-Backup-and-Restore.md)   
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)  
  
  