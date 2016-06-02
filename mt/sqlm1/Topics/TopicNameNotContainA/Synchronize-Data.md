---
title: Synchronize Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
---
# Synchronize Data
  Synchronizing data refers to the process of data and schema changes being propagated between the Publisher and Subscribers after the initial snapshot has been applied at the Subscriber. Synchronization can occur:  
  
-   Continuously, which is typical for transactional replication.  
  
-   On demand, which is typical for merge replication.  
  
-   On a schedule, which is typical for snapshot replication.  
  
 When a subscription is synchronized, different processes occur based on the type of replication you are using:  
  
-   Snapshot replication. Synchronization means that the Distribution Agent reapplies the snapshot at the Subscriber so that schema and data at the subscription database is consistent with the publication database.  
  
     If modifications to data or schema have been made at the Publisher, a new snapshot must be generated in order to propagate modifications to the Subscriber.  
  
-   Transactional replication. Synchronization means that the Distribution Agent transfers updates, inserts, deletes, and any other changes from the distribution database to the Subscriber.  
  
-   Merge replication. Synchronization means that the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber. Conflicts, if any, are detected and resolved. Data is converged, and the Publisher and all Subscribers eventually end up with the same data values. If conflicts were detected and resolved, work that was committed by some of the users is changed to resolve the conflict according to policies you define.  
  
 Snapshot publications completely refresh the schema at the Subscriber every time synchronization occurs, so all schema changes are applied to the Subscriber. Transactional replication and merge replication also support the most common schema changes. For more information, see [Make Schema Changes on Publication Databases](../../Topics\TopicNameNotContainA/Make-Schema-Changes-on-Publication-Databases.md).  
  
 To synchronize a push subscription, see [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
 To synchronize a pull subscription, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
 To set synchronization schedules, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
 **To view and resolve synchronization conflicts**  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../Topic/View%20and%20Resolve%20Data%20Conflicts%20for%20Merge%20Publications%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../Topic/View%20Data%20Conflicts%20for%20Transactional%20Publications%20\(SQL%20Server%20Management%20Studio\).md)  
  
## Executing Code During Synchronization  
 Replication supports two methods of executing code during synchronization  
  
-   On demand script execution is supported for transactional replication and merge replication. Using on demand script execution you can specify a SQL script to run during synchronization. The script is copied to the Subscriber and executed using **sqlcmd** at the beginning of the synchronization process. The script does not have access to the replicated changes as they are applied to the Subscriber. For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../Topic/Execute%20Scripts%20During%20Synchronization%20\(Replication%20Transact-SQL%20Programming\).md).  
  
-   Business logic handlers are supported for merge replication. Using the business logic handler framework you can write a managed code assembly that is called during the merge synchronization process. The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors. For more information, see [Execute Business Logic During Merge Synchronization](../../Topics\TopicNameNotContainA/Execute-Business-Logic-During-Merge-Synchronization.md).  
  
## See Also  
 [Detect and Resolve Merge Replication Conflicts](../../Topics\TopicNameNotContainA/Detect-and-Resolve-Merge-Replication-Conflicts.md)  
  
  