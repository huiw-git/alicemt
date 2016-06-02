---
title: The Transaction Log (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-transaction-log
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7be5ac5-4c8e-4d0a-b114-939eb97dac4d
---
# The Transaction Log (SQL Server)
  Every [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database has a transaction log that records all transactions and the database modifications made by each transaction. The transaction log must be truncated on a regular basis to keep it from filling up. However, some factors can delay log truncation, so monitoring log size is important. Some operations can be minimally logged to reduce their impact on transaction log size.  
  
 The transaction log is a critical component of the database and, if there is a system failure, the transaction log might be required to bring your database back to a consistent state. The transaction log should never be deleted or moved unless you fully understand the ramifications of doing this.  
  
> [!NOTE]  
>  Known good points from which to begin applying transaction logs during database recovery are created by checkpoints. For more information, see [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md).  
  
 **In this Topic:**  
  
-   [Benefits: Operations Supported by the Transaction Log](#Benefits)  
  
-   [Transaction Log Truncation](#Truncation)  
  
-   [Factors That Can Delay Log Truncation](#FactorsThatDelayTruncation)  
  
-   [Operations That Can Be Minimally Logged](#MinimallyLogged)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Benefits"></a> Benefits: Operations Supported by the Transaction Log  
 The transaction log supports the following operations:  
  
-   Recovery of individual transactions.  
  
-   Recovery of all incomplete transactions when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started.  
  
-   Rolling a restored database, file, filegroup, or page forward to the point of failure.  
  
-   Supporting transactional replication.  
  
-   Supporting high availability and disaster recovery solutions: [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], database mirroring, and log shipping.  
  
##  <a name="Truncation"></a> Transaction Log Truncation  
 Log truncation frees space in the log file for reuse by the transaction log. Log truncation is essential to keep the log from filling. Log truncation deletes inactive virtual log files from the logical transaction log of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, freeing space in the logical log for reuse by the Physical transaction log. If a transaction log were never truncated, it would eventually fill all the disk space that is allocated to its physical log files.  
  
 To avoid this problem, unless log truncation is being delayed for some reason, truncation occurs automatically after the following events:  
  
-   Under the simple recovery model, after a checkpoint.  
  
-   Under the full recovery model or bulk\-logged recovery model, if a checkpoint has occurred since the previous backup, truncation occurs after a log backup \(unless it is a copy\-only log backup\).  
  
 For more information, see [Factors That Can Delay Log Truncation](#FactorsThatDelayTruncation), later in this topic.  
  
> [!NOTE]  
>  Log truncation does not reduce the size of the physical log file. To reduce the physical size of a physical log file, you need to shrink the log file. For information about shrinking the size of the physical log file, see [Manage the Size of the Transaction Log File](../../Topics\TopicNameNotContainA/Manage-the-Size-of-the-Transaction-Log-File.md).  
  
##  <a name="FactorsThatDelayTruncation"></a> Factors That Can Delay Log Truncation  
 When log records remain active for a long time transaction log truncation is delayed, and potentially the transaction log can fill up.  
  
> [!IMPORTANT]  
>  For information about how to respond to a full transaction log, see [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../Topic/Troubleshoot%20a%20Full%20Transaction%20Log%20\(SQL%20Server%20Error%209002\).md).  
  
 Log truncation can be delayed by a variety of factors. You can discover what, if anything, is preventing log truncation by querying the **log\_reuse\_wait** and **log\_reuse\_wait\_desc** columns of the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view. The following table describes the values of these columns.  
  
|log\_reuse\_wait value|log\_reuse\_wait\_desc value|Description|  
|----------------------------|----------------------------------|-----------------|  
|0|NOTHING|Currently there are one or more reusable virtual log files.|  
|1|CHECKPOINT|No checkpoint has occurred since the last log truncation, or the head of the log has not yet moved beyond a virtual log file. \(All recovery models\)<br /><br /> This is a routine reason for delaying log truncation. For more information, see [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md).|  
|2|LOG\_BACKUP|A log backup is required before the transaction log can be truncated. \(Full or bulk\-logged recovery models only\)<br /><br /> When the next log backup is completed, some log space might become reusable.|  
|3|ACTIVE\_BACKUP\_OR\_RESTORE|A data backup or a restore is in progress \(all recovery models\).<br /><br /> If a data backup is preventing log truncation, canceling the backup operation might help the immediate problem.|  
|4|ACTIVE\_TRANSACTION|A transaction is active \(all recovery models\):<br /><br /> A long\-running transaction might exist at the start of the log backup. In this case, freeing the space might require another log backup. Note that long\-running transactions prevent log truncation under all recovery models, including the simple recovery model, under which the transaction log is generally truncated on each automatic checkpoint.<br /><br /> A transaction is deferred. A *deferred transaction* is effectively an active transaction whose rollback is blocked because of some unavailable resource. For information about the causes of deferred transactions and how to move them out of the deferred state, see [Deferred Transactions &#40;SQL Server&#41;](../Topic/Deferred%20Transactions%20\(SQL%20Server\).md).|  
|5|DATABASE\_MIRRORING|Database mirroring is paused, or under high\-performance mode, the mirror database is significantly behind the principal database. \(Full recovery model only\)<br /><br /> For more information, see [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md).|  
|6|REPLICATION|During transactional replications, transactions relevant to the publications are still undelivered to the distribution database. \(Full recovery model only\)<br /><br /> For information about transactional replication, see [SQL Server Replication](../../Topics\TopicNameNotContainA/SQL-Server-Replication.md).|  
|7|DATABASE\_SNAPSHOT\_CREATION|A database snapshot is being created. \(All recovery models\)<br /><br /> This is a routine, and typically brief, cause of delayed log truncation.|  
|8|LOG\_SCAN|A log scan is occurring. \(All recovery models\)<br /><br /> This is a routine, and typically brief, cause of delayed log truncation.|  
|9|AVAILABILITY\_REPLICA|A secondary replica of an availability group is applying transaction log records of this database to a corresponding secondary database. \(Full recovery model\)<br /><br /> For more information, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md).|  
|10|—|For internal use only|  
|11|—|For internal use only|  
|12|—|For internal use only|  
|13|OLDEST\_PAGE|If a database is configured to use indirect checkpoints, the oldest page on the database might be older than the checkpoint LSN. In this case, the oldest page can delay log truncation. \(All recovery models\)<br /><br /> For information about indirect checkpoints, see [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md).|  
|14|OTHER\_TRANSIENT|This value is currently not used.|  
  
##  <a name="MinimallyLogged"></a> Operations That Can Be Minimally Logged  
 *Minimal logging* involves logging only the information that is required to recover the transaction without supporting point\-in\-time recovery. This topic identifies the operations that are minimally logged under the bulk\-logged recovery model \(as well as under the simple recovery model, except when a backup is running\).  
  
> [!NOTE]  
>  Minimal logging is not supported for memory\-optimized tables.  
  
> [!NOTE]  
>  Under the full recovery model, all bulk operations are fully logged. However, you can minimize logging for a set of bulk operations by switching the database to the bulk\-logged recovery model temporarily for bulk operations. Minimal logging is more efficient than full logging, and it reduces the possibility of a large\-scale bulk operation filling the available transaction log space during a bulk transaction. However, if the database is damaged or lost when minimal logging is in effect, you cannot recover the database to the point of failure.  
  
 The following operations, which are fully logged under the full recovery model, are minimally logged under the simple and bulk\-logged recovery model:  
  
-   Bulk import operations \([bcp](../../Topics\TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](../Topic/BULK%20INSERT%20\(Transact-SQL\).md), and [INSERT... SELECT](../Topic/INSERT%20\(Transact-SQL\).md)\). For more information about when bulk import into a table is minimally logged, see [Prerequisites for Minimal Logging in Bulk Import](../../Topics\TopicNameNotContainA/Prerequisites-for-Minimal-Logging-in-Bulk-Import.md).  
  
    > [!NOTE]  
    >  When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.  
  
-   SELECT [INTO](../Topic/INTO%20Clause%20\(Transact-SQL\).md) operations.  
  
    > [!NOTE]  
    >  When transactional replication is enabled, SELECT INTO operations are fully logged even under the Bulk Logged recovery model.  
  
-   Partial updates to large value data types, using the .WRITE clause in the [UPDATE](../Topic/UPDATE%20\(Transact-SQL\).md) statement when inserting or appending new data. Note that minimal logging is not used when existing values are updated. For more information about large value data types, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md).  
  
-   [WRITETEXT](../Topic/WRITETEXT%20\(Transact-SQL\).md) and [UPDATETEXT](../Topic/UPDATETEXT%20\(Transact-SQL\).md) statements when inserting or appending new data into the **text**, **ntext**, and **image** data type columns. Note that minimal logging is not used when existing values are updated.  
  
    > [!NOTE]  
    >  The WRITETEXT and UPDATETEXT statements are deprecated, so you should avoid using them in new applications.  
  
-   If the database is set to the simple or bulk\-logged recovery model, some index DDL operations are minimally logged whether the operation is executed offline or online. The minimally logged index operations are as follows:  
  
    -   [CREATE INDEX](../Topic/CREATE%20INDEX%20\(Transact-SQL\).md) operations \(including indexed views\).  
  
    -   [ALTER INDEX](../Topic/ALTER%20INDEX%20\(Transact-SQL\).md) REBUILD or DBCC DBREINDEX operations.  
  
        > [!NOTE]  
        >  The DBCC DBREINDEX statement is deprecated so you should avoid using it in new applications.  
  
    -   DROP INDEX new heap rebuild \(if applicable\).  
  
        > [!NOTE]  
        >  Index page deallocation during a [DROP INDEX](../Topic/DROP%20INDEX%20\(Transact-SQL\).md) operation is always fully logged.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **Managing the transaction log**  
  
-   [Manage the Size of the Transaction Log File](../../Topics\TopicNameNotContainA/Manage-the-Size-of-the-Transaction-Log-File.md)  
  
-   [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../Topic/Troubleshoot%20a%20Full%20Transaction%20Log%20\(SQL%20Server%20Error%209002\).md)  
  
 **Backing Up the Transaction Log \(Full Recovery Model\)**  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
 **Restoring the Transaction Log \(Full Recovery Model\)**  
  
-   [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)  
  
## See Also  
 [Control Transaction Durability](../../Topics\TopicNameNotContainA/Control-Transaction-Durability.md)   
 [Prerequisites for Minimal Logging in Bulk Import](../../Topics\TopicNameNotContainA/Prerequisites-for-Minimal-Logging-in-Bulk-Import.md)   
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md)   
 [View or Change the Properties of a Database](../../Topics\TopicNameContainA/View-or-Change-the-Properties-of-a-Database.md)   
 [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md)  
  
  