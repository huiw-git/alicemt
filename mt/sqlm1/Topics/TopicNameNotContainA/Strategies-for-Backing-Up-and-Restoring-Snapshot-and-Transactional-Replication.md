---
title: Strategies for Backing Up and Restoring Snapshot and Transactional Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8afcdbc-55db-4916-a219-19454f561f9e
---
# Strategies for Backing Up and Restoring Snapshot and Transactional Replication
  When you design a backup and restore strategy for snapshot and transactional replication, there are three areas to consider:  
  
-   Which databases to back up.  
  
-   Backup settings for transactional replication.  
  
-   The steps that are required to restore a database. These depend on the type of replication and options chosen.  
  
 This topic covers each of these areas in the next three sections. For information about backup and restore for Oracle publishing, see [Backup and Restore for Oracle Publishers](../../Topics\TopicNameNotContainA/Backup-and-Restore-for-Oracle-Publishers.md).  
  
## Backing up Databases  
 For snapshot and transactional replication, you should regularly back up the following databases:  
  
-   The publication database at the Publisher.  
  
-   The distribution database at the Distributor.  
  
-   The subscription database at each Subscriber.  
  
-   The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers. These databases should be backed up at the same time as each other and the relevant replication database. For example, back up the **master** and **msdb** databases at the Publisher at the same time that you back up the publication database. If the publication database is restored, make sure that the **master** and **msdb** databases are consistent with the publication database with regard to replication configuration and settings.  
  
 If you perform regular log backups, any replication\-related changes should be captured in the log backups. If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed. For more information, see [Common Actions Requiring an Updated Backup](../../Topics\TopicNameNotContainA/Common-Actions-Requiring-an-Updated-Backup.md).  
  
## Backup Settings for Transactional Replication  
 Transactional replication includes using the **sync with backup** option, which can be set on the distribution database and the publication database:  
  
-   We recommend that you always set this option on the distribution database.  
  
     Setting this option on the distribution database ensures that transactions in the log of the publication database will not be truncated until they have been backed up at the distribution database. The distribution database can be restored to the last backup, and any missing transactions are delivered from the publication database to the distribution database. Replication continues unaffected.  
  
     Setting this option on the distribution database does not affect replication latency. However, the option will delay the truncation of the log on the publication database until the corresponding transactions in the distribution database have been backed up. \(This can create a larger transaction log in the publication database.\)  
  
-   We recommend that you set this option on the publication database if your application can tolerate additional latency.  
  
     Setting this option on the publication database ensures that transactions are not delivered to the distribution database until they are backed up at the publication database. The last publication database backup can then be restored at the Publisher without any chance of the distribution database having transactions that the restored publication database does not have.  
  
     Latency and throughput are affected because transactions cannot be delivered to the distribution database until they have been backed up at the Publisher. For example, if the transaction log is backed up every five minutes, there is an additional five minutes of latency between when a transaction is committed at the Publisher and when the transaction is delivered to the distribution database, and subsequently the Subscriber.  
  
    > [!NOTE]  
    >  The **sync with backup** option ensures consistency between the publication database and the distribution database, but the option does not guarantee against data loss. For example, if the transaction log is lost, transactions that have been committed since the last transaction log backup will not be available in the publication database or the distribution database. This is the same behavior as a nonreplicated database.  
  
 **To set the sync with backup option**  
  
-   Replication [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] programming: [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](../Topic/Enable%20Coordinated%20Backups%20for%20Transactional%20Replication%20\(Replication%20Transact-SQL%20Programming\).md)  
  
## Restoring Databases Involved in Replication  
 You can restore all databases in a replication topology if recent backups are available and the appropriate steps are followed. The restore steps for the publication database depend on the type of replication and options that are used; however, the restore steps for all other databases are independent of the type and options.  
  
 Replication supports restoring replicated databases to the same server and database from which the backup was created. If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved. In this case, you must re\-create all publications and subscriptions after backups are restored.  
  
### Publisher  
 There are restore steps provided for the following types of replication:  
  
-   Snapshot replication  
  
-   Read\-only transactional replication  
  
-   Transactional replication with updating subscriptions  
  
-   Peer\-to\-peer transactional replication  
  
 The restore of the **msdb** and **master** databases, which are also covered in this section, is the same for all four types.  
  
#### Publication Database: Snapshot Replication  
  
1.  Restore the latest backup of the publication database. Go to step 2.  
  
2.  Does the publication database backup contain the latest configuration for all publications and subscriptions? If yes, the restore is completed. If no, go to step 3.  
  
3.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. Restore is completed.  
  
     For more information about how to remove replication, see [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
#### Publication Database: Read\-Only Transactional Replication  
  
1.  Restore the latest backup of the publication database. Go to step 2.  
  
2.  Was the **sync with backup** setting enabled on the publication database before the failure? If yes, go to step 3; if no, go to step 5.  
  
     If the setting is enabled, the query `SELECT DATABASEPROPERTYEX('<PublicationDatabaseName>', 'IsSyncWithBackup')` returns '1'.  
  
3.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, the restore is completed. If no, go to step 4.  
  
4.  The configuration information in the restored publication database is not up\-to\-date. Therefore, you must make sure that the Subscribers have all outstanding commands in the distribution database, and then drop and re\-create the replication configuration.  
  
    1.  Run the Distribution Agent until all Subscribers are synchronized with the outstanding commands in the distribution database. Verify that all commands are delivered to Subscribers by using the **Undistributed Commands** tab in Replication Monitor or by querying the [MSdistribution\_status](../Topic/MSdistribution_status%20\(Transact-SQL\).md) view in the distribution database. Go to step b.  
  
         For more information about how to run the Distribution Agent, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
         For more information about how to verify commands, see [View Replicated Commands and Other Information in the Distribution Database &#40;Replication Transact-SQL Programming&#41;](../Topic/View%20Replicated%20Commands%20and%20Other%20Information%20in%20the%20Distribution%20Database%20\(Replication%20Transact-SQL%20Programming\).md) and [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
    2.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. When you re\-create subscriptions, specify that the Subscriber already has the data. The restore is completed.  
  
         For more information about how to remove replication, see [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
         For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
5.  The **sync with backup** option was not set on the publication database. Therefore, transactions that were not included in the restored backup might have been delivered to the Distributor and Subscribers. You must now make sure that Subscribers have all outstanding commands in the distribution database, and then manually apply to the publication database any transactions that are not included in the restored backup.  
  
    > [!IMPORTANT]  
    >  Performing this process can cause published tables to be restored to a point in time that is more recent than the point in time of other nonpublished tables that are restored from the backup.  
  
    1.  Run the Distribution Agent until all Subscribers are synchronized with the outstanding commands in the distribution database. Verify that all commands are delivered to Subscribers by using the **Undistributed Commands** tab in Replication Monitor or by querying the [MSdistribution\_status](../Topic/MSdistribution_status%20\(Transact-SQL\).md) view in the distribution database. Go to step b.  
  
         For more information about how to run the Distribution Agent, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
         For more information about how to verify commands, see [View Replicated Commands and Other Information in the Distribution Database &#40;Replication Transact-SQL Programming&#41;](../Topic/View%20Replicated%20Commands%20and%20Other%20Information%20in%20the%20Distribution%20Database%20\(Replication%20Transact-SQL%20Programming\).md) and [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
    2.  Use the [tablediff utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md) or another tool to manually synchronize the Publisher with the Subscriber. This enables you to recover data from the subscription database that was not contained in the publication database backup. Go to step c.  
  
         For more information about the **tablediff** utility, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](../Topic/Compare%20Replicated%20Tables%20for%20Differences%20\(Replication%20Programming\).md).  
  
    3.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, execute the [sp\_replrestart](../Topic/sp_replrestart%20\(Transact-SQL\).md) stored procedure to resynchronize the Publisher metadata with the Distributor metadata. The restore is completed. If no, go to step d.  
  
    4.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. When you re\-create subscriptions, specify that the Subscriber already has the data. The restore is completed.  
  
         For more information about how to remove replication, see [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
         For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
#### Publication Database: Transactional Replication with Updating Subscriptions  
  
1.  Restore the latest backup of the publication database. Go to step 2.  
  
2.  Run the Distribution Agent until all Subscribers are synchronized with the outstanding commands in the distribution database. Verify that all commands are delivered to Subscribers by using the **Undistributed Commands** tab in Replication Monitor, or by querying the [MSdistribution\_status](../Topic/MSdistribution_status%20\(Transact-SQL\).md) view in the distribution database. Go to step 3.  
  
     For more information about how to run the Distribution Agent, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
     For more information about how to verify commands, see [View Replicated Commands and Other Information in the Distribution Database &#40;Replication Transact-SQL Programming&#41;](../Topic/View%20Replicated%20Commands%20and%20Other%20Information%20in%20the%20Distribution%20Database%20\(Replication%20Transact-SQL%20Programming\).md) and [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
3.  If you are using queued updating subscriptions, connect to each Subscriber and delete all rows from the [MSreplication_queue &#40;Transact-SQL&#41;](../Topic/MSreplication_queue%20\(Transact-SQL\).md) table in the subscription database. Go to step 4.  
  
    > [!NOTE]  
    >  If you are using queued updating subscriptions and any tables contain identity columns, you must make sure that the correct identity ranges are assigned after a restore. For more information, see [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
4.  You must now make sure that Subscribers have all outstanding commands in the distribution database, and then manually apply to the publication database any transactions that are not included in the restored backup.  
  
    > [!IMPORTANT]  
    >  Performing this process can cause published tables to be restored to a point in time that is more recent than the point in time of other nonpublished tables that are restored from the backup.  
  
    1.  Run the Distribution Agent until all Subscribers are synchronized with the outstanding commands in the distribution database. Verify that all commands are delivered to Subscribers by using Replication Monitor or by querying the [MSdistribution\_status](../Topic/MSdistribution_status%20\(Transact-SQL\).md) view in the distribution database. Go to step b.  
  
    2.  Use the [tablediff Utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md) or another tool to manually synchronize the Publisher with the Subscriber. This enables you to recover data from the subscription database that was not contained in the publication database backup. Go to step c.  
  
         For more information about the **tablediff** utility, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](../Topic/Compare%20Replicated%20Tables%20for%20Differences%20\(Replication%20Programming\).md).  
  
    3.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, execute the [sp\_replrestart](../Topic/sp_replrestart%20\(Transact-SQL\).md) stored procedure to resynchronize the Publisher metadata with the Distributor metadata. The restore is completed. If no, go to step d.  
  
    4.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. When you re\-create subscriptions, specify that the Subscriber already has the data. The restore is completed.  
  
         For more information about how to remove replication, see and [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
         For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
#### Publication Database: Peer\-to\-Peer Transactional Replication  
 In the following steps, publication databases **A**, **B**, and **C** are in a peer\-to\-peer transactional replication topology. Databases **A** and **C** are online and functioning properly; database **B** is the database to be restored. The process described here, especially steps 7, 10, and 11, is very similar to the process required to add a node to a peer\-to\-peer topology. The most straightforward way to perform these steps is to use the Configure Peer\-to\-Peer Topology Wizard, but you can also use stored procedures.  
  
1.  Run the Distribution Agents to synchronize the subscriptions at databases **A** and **C**. Go to step 2.  
  
     For more information about how to run the Distribution Agent, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
2.  If the distribution database that **B** uses is still available, run Distribution Agents to synchronize subscriptions between databases **B** and **A** and databases and B and **C**. Go to step 3.  
  
3.  Remove metadata from the distribution database that **B** uses by executing [sp\_removedistpublisherdbreplication](../Topic/sp_removedistpublisherdbreplication%20\(Transact-SQL\).md) at the distribution database for **B**. Go to step 4.  
  
4.  At databases **A** and **C**, drop the subscriptions to the publication at database **B**. Go to step 5.  
  
     For more information about how to drop subscriptions, see [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md).  
  
5.  Perform a log backup or full backup of database **A**. Go to step 6.  
  
6.  Restore the backup of database **A** at database **B**. Database **B** now has the data from database **A**, but not the replication configuration. When you restore a backup to another server, replication is removed; therefore, replication has been removed from database **B**. Go to step 7.  
  
7.  Re\-create the publication at database **B**, and then re\-create subscriptions between databases **A** and **B**. \(Subscriptions that involve database **C** are handled at a later stage.\).  
  
    1.  Re\-create the publication at database **B**. Go to step b.  
  
    2.  Re\-create the subscription at database **B** to the publication at database **A**, specifying that the subscription should be initialized with a backup \(a value of **initialize with backup** for the **@sync\_type** parameter of [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md)\). Go to step c.  
  
    3.  Re\-create the subscription at database **A** to the publication at database **B**, specifying that the Subscriber already has the data \(a value of **replication support only** for the **@sync\_type** parameter of [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md)\). Go to step 8.  
  
8.  Run the Distribution Agents to synchronize the subscriptions at databases **A** and **B**. If there are any identity columns in published tables, go to step 9. If not, go to step 10.  
  
9. After the restore, the identity range that you assigned for each table in database **A** would also be used in database **B**. Make sure that the restored database **B** has received all changes from the failed database **B** that were propagated to database **A** and database **C**; and then reseed the identity range for each table.  
  
    1.  Execute [sp\_requestpeerresponse](../Topic/sp_requestpeerresponse%20\(Transact-SQL\).md) at database **B** and retrieve the output parameter **@request\_id**. Go to step b.  
  
    2.  By default, the Distribution Agent is set to run continuously; therefore, tokens should be sent to all nodes automatically. If the Distribution Agent is not running in continuous mode, run the agent. For more information, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md). Go to step c.  
  
    3.  Execute [sp\_helppeerresponses](../Topic/sp_helppeerresponses%20\(Transact-SQL\).md), providing the **@request\_id** value retrieved in step b. Wait until all nodes indicate they have received the peer request. Go to step d.  
  
    4.  Use [DBCC CHECKIDENT](../Topic/DBCC%20CHECKIDENT%20\(Transact-SQL\).md) to reseed each table in database **B** to make sure that an appropriate range is used. Go to step 10.  
  
     For more information about how to manage identity ranges, see the "Assigning ranges for manual identity range management" section of [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
10. At this point, database **B** and database **C** are not directly connected, but they will receive changes through database **A**. If the topology contains any nodes that are running [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], go to step 11; otherwise, go to step 12.  
  
11. Quiesce the system, and then re\-create the subscription between databases **B** and **C**. Quiescing a system involves stopping activity on published tables at all nodes and making sure of that each node has received all changes from all other nodes.  
  
    1.  Stop all activity on published tables in the peer\-to\-peer topology. Go to step b.  
  
    2.  Execute [sp\_requestpeerresponse](../Topic/sp_requestpeerresponse%20\(Transact-SQL\).md) at database **B** and retrieve the output parameter **@request\_id**. Go to step c.  
  
    3.  By default, the Distribution Agent is set to run continuously; therefore, tokens should be sent to all nodes automatically. If the Distribution Agent is not running in continuous mode, run the agent. Go to step d.  
  
    4.  Execute [sp\_helppeerresponses](../Topic/sp_helppeerresponses%20\(Transact-SQL\).md), providing the **@request\_id** value retrieved in step b. Wait until all nodes indicate they have received the peer request. Go to step e.  
  
    5.  Re\-create the subscription at database **B** to the publication at database **C**, specifying that the Subscriber already has the data. Go to step b.  
  
    6.  Re\-create the subscription at database **C** to the publication at database **B**, specifying that the Subscriber already has the data. Go to step 13.  
  
12. Re\-create the subscription between databases **B** and **C**:  
  
    1.  At database **B**, query the [MSpeer\_lsns](../Topic/MSpeer_lsns%20\(Transact-SQL\).md) table to retrieve the log sequence number \(LSN\) of the most recent transaction that database **B** has received from database **C**.  
  
    2.  Re\-create the subscription at database **B** to the publication at database **C**, specifying that the subscription should be initialized based on LSN \(a value of **initialize from lsn** for the **@sync\_type** parameter of [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md)\). Go to step b.  
  
    3.  Re\-create the subscription at database **C** to the publication at database **B**, specifying that the Subscriber already has the data. Go to step 13.  
  
13. Run the Distribution Agents to synchronize the subscriptions at databases **B** and **C**. The restore is completed.  
  
#### msdb Database \(Publisher\)  
  
1.  Restore the latest backup of the **msdb** database.  
  
2.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, recovery is completed. If no, go to step 3.  
  
3.  Re\-create the subscription cleanup job from your replication scripts. Recovery is completed.  
  
#### master Database \(Publisher\)  
  
1.  Restore the latest backup of the **master** database.  
  
2.  Make sure that the database is consistent with the publication database with regard to replication configuration and settings.  
  
### Databases at the Distributor  
  
#### Distribution Database  
  
1.  Restore the latest backup of the distribution database.  
  
2.  Was the **sync with backup** setting enabled on the distribution database before the failure? If yes, go to step 3; if no, go to step 4.  
  
     If the setting is enabled, the query `SELECT DATABASEPROPERTYEX('<DistributionDatabaseName>', 'IsSyncWithBackup')` returns '1'.  
  
3.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, recovery is completed. If no, go to step 4.  
  
4.  Either the configuration information in the restored distribution database is not up\-to\-date, or the **sync with backup** option was not set on the distribution database. \(After the restore, the distribution database might be missing transactions that were committed at the Publisher but have not yet been delivered to Subscribers.\) Drop and re\-create replication, and then run validation.  
  
    1.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. When you re\-create subscriptions, specify that the Subscriber already has the data. Go to step b.  
  
         For more information about how to remove replication, see [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
         For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
    2.  Mark all publications for validation. Reinitialize any subscriptions that fail validation. Recovery is completed.  
  
         For more information about validation, see [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md). For more information about reinitialization, see [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
#### msdb Database \(Distributor\)  
  
1.  Restore the latest backup of the **msdb** database.  
  
2.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all publications and subscriptions? If yes, recovery is completed. If no, go to step 3.  
  
3.  Remove the replication configuration from the Publisher, Distributor and Subscribers, and then re\-create the configuration. When you re\-create subscriptions, specify that the Subscriber already has the data. Go to step 4.  
  
     For more information about how to remove replication, see [sp_removedbreplication &#40;Transact-SQL&#41;](../Topic/sp_removedbreplication%20\(Transact-SQL\).md).  
  
     For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
4.  Mark all publications for validation. Reinitialize any subscriptions that fail validation. Recovery is completed.  
  
     For more information about validation, see [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md). For more information about reinitialization, see [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
#### master Database \(Distributor\)  
  
1.  Restore the latest backup of the **master** database.  
  
2.  Make sure that the database is consistent with the publication database with regard to replication configuration and settings.  
  
### Databases at the Subscriber  
  
#### Subscription Database  
  
1.  Is the latest subscription database backup more recent than the minimum distribution retention setting on the distribution database? \(This determines whether the Distributor still has all the commands that are required to bring the Subscriber up\-to\-date.\) If yes, go to step 2. If no, reinitialize the subscription. Recovery is completed.  
  
     To determine the maximum distribution retention setting, execute [sp\_helpdistributiondb](../Topic/sp_helpdistributiondb%20\(Transact-SQL\).md) and retrieve the value from the **max\_distretention** column \(this value is in hours\).  
  
     For more information about how to reinitialize a subscription, see [Reinitialize a Subscription](../../Topics\TopicNameContainA/Reinitialize-a-Subscription.md).  
  
2.  Restore the latest subscription database backup. Go to step 3.  
  
3.  If the subscription database contains only push subscriptions, go to step 4. If the subscription database contains any pull subscriptions, ask the following questions: Is the subscription information current? Does the database include all tables and options that were set at the time of failure. If yes, go to step 4. If no, reinitialize the subscription. Recovery is completed.  
  
4.  To synchronize the Subscriber, run the Distribution Agent. Recovery is completed.  
  
     For more information about how to run the Distribution Agent, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md) and [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
#### msdb Database \(Subscriber\)  
  
1.  Restore the latest backup of the **msdb** database. Are pull subscriptions used at this Subscriber? If no, the restore is completed. If yes, go to step 2.  
  
2.  Is the restored backup complete and up\-to\-date? Does it contain the latest configuration for all pull subscriptions? If yes, recovery is completed. If no, go to step 3.  
  
3.  Drop and re\-create the pull subscriptions. When you re\-create the subscriptions, specify that the Subscriber already has the data. The restore is completed.  
  
     For more information about how to drop subscriptions, see [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md).  
  
     For more information about how to specify that the Subscriber already has the data, see [Initialize a Subscription Manually](../../Topics\TopicNameContainA/Initialize-a-Subscription-Manually.md).  
  
#### master Database \(Subscriber\)  
  
1.  Restore the latest backup of the **master** database.  
  
2.  Make sure that the database is consistent with the publication database with regard to replication configuration and settings.  
  
## See Also  
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Back Up and Restore Replicated Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)   
 [Initialize a Subscription](../../Topics\TopicNameContainA/Initialize-a-Subscription.md)   
 [Synchronize Data](../../Topics\TopicNameNotContainA/Synchronize-Data.md)  
  
  