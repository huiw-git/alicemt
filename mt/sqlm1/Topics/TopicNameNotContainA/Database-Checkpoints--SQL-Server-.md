---
title: Database Checkpoints (SQL Server)
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98a80238-7409-4708-8a7d-5defd9957185
---
# Database Checkpoints (SQL Server)
  This topic provides an overview of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database checkpoints. A *checkpoint* creates a known good point from which the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] can start applying changes contained in the log during recovery after an unexpected shutdown or crash.  
  
 **In this Topic:**  
  
-   [Overview of Checkpoints](#Overview)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="Overview"></a> Overview of Checkpoints  
 For performance reasons, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] performs modifications to database pages in memory—in the buffer cache—and does not write these pages to disk after every change. Rather, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] periodically issues a checkpoint on each database. A *checkpoint* writes the current in\-memory modified pages \(known as *dirty pages*\) and transaction log information from memory to disk and, also, records information about the transaction log.  
  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] supports several types of checkpoints: automatic, indirect, manual, and internal. The following table summarizes the types of checkpoints.  
  
|Name|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] Interface|Description|  
|----------|----------------------------------|-----------------|  
|Automatic|EXEC sp\_configure **'**recovery interval**','***seconds***'**|Issued automatically in the background to meet the upper time limit suggested by the **recovery interval** server configuration option. Automatic checkpoints run to completion.  Automatic checkpoints are throttled based on the number of outstanding writes and whether the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] detects an increase in write latency above 20 milliseconds.<br /><br /> For more information, see [Configure the recovery interval Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-recovery-interval-Server-Configuration-Option.md).|  
|Indirect|ALTER DATABASE … SET TARGET\_RECOVERY\_TIME **\=***target\_recovery\_time* { SECONDS &#124; MINUTES }|Issued in the background to meet a user\-specified target recovery time for a given database. The default is 0, which indicates that the database will use automatic checkpoints, whose frequency depends on the recovery interval setting of the server instance.<br /><br /> For more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../Topic/Change%20the%20Target%20Recovery%20Time%20of%20a%20Database%20\(SQL%20Server\).md).|  
|Manual|CHECKPOINT \[ *checkpoint\_duration* \]|Issued when you execute a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] CHECKPOINT command. The manual checkpoint occurs in the current database for your connection. By default, manual checkpoints run to completion. Throttling works the same way as for automatic checkpoints.  Optionally, the *checkpoint\_duration* parameter specifies a requested amount of time, in seconds, for the checkpoint to complete.<br /><br /> For more information, see [CHECKPOINT &#40;Transact-SQL&#41;](../Topic/CHECKPOINT%20\(Transact-SQL\).md).|  
|Internal|None.|Issued by various server operations such as backup and database\-snapshot creation to guarantee that disk images match the current state of the log.|  
  
> [!NOTE]  
>  The **\-k**[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] advanced setup option enables a database administrator to throttle checkpoint I\/O behavior based on the throughput of the I\/O subsystem for some types of checkpoints. The **\-k** setup option applies to automatic checkpoints and any otherwise unthrottled manual and internal checkpoints.  
  
 For automatic, manual, and internal checkpoints, only modifications made after the latest checkpoint need to be rolled forward during database recovery. This reduces the time required to recover a database.  
  
> [!IMPORTANT]  
>  Long\-running uncommitted transactions increase recovery time for all types of checkpoints.  
  
 [&#91;Top&#93;](#Top)  
  
 **In This Section:**  
  
-   [Interaction of the TARGET\_RECOVERY\_TIME and 'recovery interval' Options](#InteractionBwnSettings)  
  
-   [Automatic Checkpoints](#AutomaticChkpt)  
  
-   [Indirect Checkpoints](#IndirectChkpt)  
  
-   [Internal Checkpoint](#EventsCausingChkpt)  
  
###  <a name="InteractionBwnSettings"></a> Interaction of the TARGET\_RECOVERY\_TIME and 'recovery interval' Options  
 The following table summarizes the interaction between the server\-wide **sp\_configure'**recovery interval**'** setting and the database\-specific ALTER DATABASE … TARGET\_RECOVERY\_TIME setting.  
  
|TARGET\_RECOVERY\_TIME|'recovery interval'|Type of Checkpoint Used|  
|----------------------------|-------------------------|-----------------------------|  
|0|0|automatic checkpoints whose target recovery interval is 1 minute.|  
|0|\>0|Automatic checkpoints whose target recovery interval is specified by the user defined setting of the **sp\_configurerecovery interval** option.|  
|\>0|Not applicable.|Indirect checkpoints whose target recovery time is determined by the TARGET\_RECOVERY\_TIME setting, expressed in seconds.|  
  
###  <a name="AutomaticChkpt"></a> Automatic Checkpoints  
 An automatic checkpoint occurs each time that  the number of log records reaches the number the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] estimates it can process during the time specified in the **recovery interval** server configuration option. In every database without a user\-defined target recovery time, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] generates automatic checkpoints. The frequency of automatic checkpoints depends on the **recovery interval** advanced server configuration option, which specifies the maximum time that a given server instance should use to recover a database during a system restart. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] estimates the maximum number of log records it can process within the recovery interval. When a database that is using automatic checkpoints reaches this maximum number of log records, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] issues an checkpoint on the database. The time interval between automatic checkpoints can be highly variable. A database with a substantial transaction workload will have more frequent checkpoints than a database that is used primarily for read\-only operations.  
  
 Also, under the simple recovery model, an automatic checkpoint is also queued if the log becomes 70 percent full.  
  
 Under the simple recovery model, unless some factor is delaying log truncation, an automatic checkpoint truncates the unused section of the transaction log. In contrast, under the full and bulk\-logged recovery models, once a log backup chain has been established, automatic checkpoints do not cause log truncation. For more information, see [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md).  
  
 After a system crash, the length of time required to recover a given database is largely dependent on the amount of random I\/O needed to redo pages that were dirty at the time of the crash. This means that the **recovery interval** setting is unreliable. It cannot determine an accurate recovery duration. Furthermore, when an automatic checkpoint is in progress, the general I\/O activity for data increases significantly and quite unpredictably.  
  
 [&#91;Top&#93;](#Top)  
  
####  <a name="PerformanceImpact"></a> Impact of Recovery Interval on Recovery Performance  
 For an online transaction processing \(OLTP\) system using short transactions, **recovery interval** is the primary factor determining recovery time. However, the **recovery interval** option does not affect the time required to undo a long\-running transaction. Recovery of a database with a long\-running transaction can take much longer than the specified in the **recovery interval** option. For example, if a long\-running transaction took two hours to perform updates before the server instance became disabled, the actual recovery takes considerably longer than the **recovery interval** value to recover the long transaction. For more information about the impact of a long running transaction on recovery time, see [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md).  
  
 Typically, the default values provides optimal recovery performance. However, changing the recovery interval might improve performance in the following circumstances:  
  
-   If recovery routinely takes significantly longer than 1 minute when long\-running transactions are not being rolled back.  
  
-   If you notice that frequent checkpoints are impairing performance on a database.  
  
 If you decide to increase the **recovery interval** setting, we recommend increasing it gradually by small increments and evaluating the effect of each incremental increase on recovery performance. This approach is important because as the **recovery interval** setting increases, database recovery takes that many times longer to complete. For example, if you change **recovery interval** 10 minutes, recovery takes approximately 10 times longer to complete than when **recovery interval** is set to 1 minute.  
  
 [&#91;Top&#93;](#Top)  
  
###  <a name="IndirectChkpt"></a> Indirect Checkpoints  
 Indirect checkpoints, new in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], provide a configurable database\-level alternative to automatic checkpoints. In the event of a system crash, indirect checkpoints provide potentially faster, more predictable recovery time than automatic checkpoints. Indirect checkpoints offer the following advantages:  
  
-   An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation. Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time. The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages. When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database. This can cause additional I\/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I\/O threshold.  
  
-   Indirect checkpoints enable you to reliably control database recovery time by factoring in the cost of random I\/O during REDO. This enables a server instance to stay within an upper\-bound on recovery times for a given database \(except when a long\-running transaction causes excessive UNDO times\).  
  
-   Indirect checkpoints reduce checkpoint\-related I\/O spiking by continually writing dirty pages to disk in the background.  
  
 However, an online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation. This is because the background writer used by indirect checkpoint sometimes increases the total write load for a server instance.  
  
 [&#91;Top&#93;](#Top)  
  
###  <a name="EventsCausingChkpt"></a> Internal Checkpoints  
 Internal Checkpoints are generated by various server components to guarantee that disk images match the current state of the log. Internal checkpoint are generated in response to the following events:  
  
-   Database files have been added or removed by using ALTER DATABASE.  
  
-   A database backup is taken.  
  
-   A database snapshot is created, whether explicitly or internally for DBCC CHECK.  
  
-   An activity requiring a database shutdown is performed. For example, AUTO\_CLOSE is ON and the last user connection to the database is closed, or a database option change is made that requires a restart of the database.  
  
-   An instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is stopped by stopping the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(MSSQLSERVER\) service . Either action  causes a checkpoint in each database in the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   Bringing a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance \(FCI\) offline.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To change the recovery interval on a server instance**  
  
-   [Configure the recovery interval Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-recovery-interval-Server-Configuration-Option.md)  
  
 **To configure indirect checkpoints on a database**  
  
-   [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../Topic/Change%20the%20Target%20Recovery%20Time%20of%20a%20Database%20\(SQL%20Server\).md)  
  
 **To issue a manual checkpoint on a database**  
  
-   [CHECKPOINT &#40;Transact-SQL&#41;](../Topic/CHECKPOINT%20\(Transact-SQL\).md)  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [Transaction Log Physical Architecture](http://technet.microsoft.com/library/ms179355.aspx) \(in [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] Books Oline\)  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)  
  
  