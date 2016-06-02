---
title: Deferred Transactions (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
---
# Deferred Transactions (SQL Server)
  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise, a corrupted transaction can become deferred if data required by rollback \(undo\) is offline during database startup. A *deferred transaction* is a transaction that is uncommitted when the roll forward phase finishes and that has encountered an error that prevents it from being rolled back. Because the transaction cannot be rolled back, it is deferred.  
  
> [!NOTE]  
>  Corrupted transactions are deferred only in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise. In other editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], a corrupted transaction causes startup to fail.  
  
 Generally, a deferred transaction occurs because, while the database was being rolled forward, an I\/O error prevented reading a page that was required by the transaction. However, an error at the file level can also cause deferred transactions. A deferred transaction can also occur when a partial restore sequence stops at a point at which transaction rollback is necessary and a transaction requires data that is offline.  
  
 User transactions that are rolling back and hit an I\/O error cause the whole database to go offline. When the database is brought back online, the redo reacquires all the locks it had and tries to roll back all the uncommitted transactions. All data modified by a transaction remains appropriately locked until the transaction can roll back. Transactions that cannot be rolled back will give up their locks when the corruption is fixed and the database restarted or, after an online restore, when the deferred transactions are resolved while the database remains online. Until that point, a deferred transaction can hold locks that prevent certain operations on the database as a whole. For example, if a deferred transaction contains a CREATE TABLE instruction, no user can create a table until the deferred transaction has been resolved.  
  
 Deferred transaction can also occur because a piecemeal restore recovers a database to a point at which one or more active transactions are affecting a filegroup that has not yet been restored and is offline. Because the transactions cannot be rolled back, they become deferred.  
  
 The following table lists the actions that cause a database to perform recovery and the outcome if an I\/O problem occurs.  
  
|Action|Resolution \(if I\/O problems occur or required data is offline\)|  
|------------|-----------------------------------------------------------------------|  
|Server start|Deferred transaction|  
|Restore|Deferred transaction|  
|Attach|Attach fails|  
|Autorestart|Deferred transaction|  
|Create database or database snapshot|Creation fails|  
|Redo on database mirroring|Deferred transaction|  
|Filegroup is offline|Deferred transaction|  
  
## Moving a Transaction Out of the DEFERRED State  
  
> [!IMPORTANT]  
>  Deferred transactions keep the transaction log active. A virtual log file that contains any deferred transactions cannot be truncated until those transactions are moved out of the deferred state. For more information about log truncation, see [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md).  
  
 To move the transaction out of the deferred state, the database must start cleanly without any I\/O errors. If deferred transactions exist, you must fix the source of the I\/O errors. The available solutions, listed in the order in which they are typically tried, are as follows:  
  
-   Restart the database. If the problem was transient, the database should start without deferred transactions.  
  
-   If the transactions were deferred because a filegroup was offline, bring the filegroup back online.  
  
     To bring an offline filegroup back online, use the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement:  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   Restore the database. After an online restore, any deferred transactions are resolved.  
  
     Under the full or bulk\-logged recovery model, if the deferred transactions were caused by only a few corrupted pages, an online page restore might resolve the errors \(where supported\).  
  
-   If you are no longer require a filegroup whose offline status is causing deferred transactions, make the offline filegroup defunct. Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.  
  
    > [!IMPORTANT]  
    >  A defunct filegroup can never be recovered.  
  
     For more information, see [Remove Defunct Filegroups &#40;SQL Server&#41;](../Topic/Remove%20Defunct%20Filegroups%20\(SQL%20Server\).md).  
  
-   If transactions were deferred because of a bad page and if a good backup of the database does not exist, use the following process to repair the database:  
  
    -   First put the database into emergency mode by executing the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement:  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         For information about emergency mode, see [Database States](../../Topics\TopicNameNotContainA/Database-States.md).  
  
    -   Then, repair the database by using the DBCC REPAIR\_ALLOW\_DATA\_LOSS option in one of the following DBCC statements: [DBCC CHECKDB](../Topic/DBCC%20CHECKDB%20\(Transact-SQL\).md), [DBCC CHECKALLOC](../Topic/DBCC%20CHECKALLOC%20\(Transact-SQL\).md), or [DBCC CHECKTABLE](../Topic/DBCC%20CHECKTABLE%20\(Transact-SQL\).md).  
  
         When DBCC encounters the bad page, DBCC deallocates it and repairs any related errors. This approach enables the database to be brought back online in a physically consistent state. However, additional data might also be lost; therefore, this approach should be used as a last resort.  
  
## See Also  
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [Remove Defunct Filegroups &#40;SQL Server&#41;](../Topic/Remove%20Defunct%20Filegroups%20\(SQL%20Server\).md)   
 [File Restores &#40;Full Recovery Model&#41;](../Topic/File%20Restores%20\(Full%20Recovery%20Model\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Restore Pages &#40;SQL Server&#41;](../Topic/Restore%20Pages%20\(SQL%20Server\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  