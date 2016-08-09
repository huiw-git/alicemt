---
title: "Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 06/29/2016
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
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# Initialize a Transactional Subscription from a Backup (Replication Transact-SQL Programming)
Although a subscription to a transactional publication is typically initialized with a snapshot, a subscription can be initialized from a backup using replication stored procedures. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
### To initialize a transactional subscriber from a backup  
  
1.  For an existing publication, ensure that the publication supports the ability to initialize from backup by executing [sp_helppublication (Transact-SQL)](assetId:///e801c3f0-dcbd-4b4a-b254-949a05f63518) at the Publisher on the publication database. Note the value of **allow_initialize_from_backup** in the result set.  
  
    -   If the value is **1**, the publication supports this functionality.  
  
    -   If the value is **0**, execute [sp_changepublication (Transact-SQL)](assetId:///c36e5865-25d5-42b7-b045-dc5036225081) at the Publisher on the publication database. Specify a value of **allow_initialize_from_backup** for **@property** and a value of **true** for **@value**.  
  
2.  For a new publication, execute [sp_addpublication (Transact-SQL)](assetId:///c7167ed1-2b7e-4824-b82b-65f4667c4407) at the Publisher on the publication database. Specify a value of **true** for **allow_initialize_from_backup**. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
    > [!WARNING]  
    >  To avoid missing subscriber data, when using **sp_addpublication** with `@allow_initialize_from_backup = N'true'`, always use `@immediate_sync = N'true'`.  
  
3.  Create a backup of the publication database using the [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1) statement.  
  
4.  Restore the backup on the Subscriber using the [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1) statement.  
  
5.  At the Publisher on the publication database, execute the stored procedure [sp_addsubscription (Transact-SQL)](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0). Specify the following parameters:  
  
    -   **@sync_type** - a value of **initialize with backup**.  
  
    -   **@backupdevicetype** - the type of backup device: **logical** (default), **disk**, or **tape**.  
  
    -   **@backupdevicename** - the logical or physical backup device to use for the restore.  
  
         For a logical device, specify the name of the backup device specified when **sp_addumpdevice** was used to create the device.  
  
         For a physical device, specify a complete path and file name, such as `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'` or `TAPE = '\\.\TAPE0'`.  
  
    -   (Optional) **@password** - a password that was provided when the backup set was created.  
  
    -   (Optional) **@mediapassword** - a password that was provided when the media set was formatted.  
  
    -   (Optional) **@fileidhint** - identifier for the backup set to be restored. For example, specifying **1** indicates the first backup set on the backup medium and **2** indicates the second backup set.  
  
    -   (Optional for tape devices) **@unload** - specify a value of **1** (default) if the tape should be unloaded from the drive after the restore is complete and **0** if it should not be unloaded.  
  
6.  (Optional) For a pull subscription, execute [sp_addpullsubscription (Transact-SQL)](assetId:///0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f) and [sp_addpullsubscription_agent (Transact-SQL)](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b) at the Subscriber on the subscription database. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
7.  (Optional) Start the Distribution Agent. For more information, see [Synchronize a Pull Subscription](../../Topics/TopicNameContainA/Synchronize-a-Pull-Subscription.md) or [Synchronize a Push Subscription](../../Topics/TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
## See Also  
 [Copy Databases with Backup and Restore](../../Topics/TopicNameNotContainA/Copy-Databases-with-Backup-and-Restore.md)   
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)