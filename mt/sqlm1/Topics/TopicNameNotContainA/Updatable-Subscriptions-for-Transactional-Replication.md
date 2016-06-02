---
title: Updatable Subscriptions for Transactional Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8eec95cb-3a11-436e-bcee-bdcd05aa5c5a
---
# Updatable Subscriptions for Transactional Replication
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
 Transactional replication supports updates at Subscribers through updatable subscriptions and peer\-to\-peer replication. The following are the two types of updatable subscriptions:  
  
-   Immediate updating. The Publisher and Subscriber must be connected to update data at the Subscriber.  
  
-   Queued updating The Publisher and Subscriber do not have to be connected to update data at the Subscriber. Updates can be made while the Subscriber or Publisher is offline.  
  
 When data is updated at a Subscriber, it is first propagated to the Publisher and then propagated to other Subscribers. If immediate updating is used, the changes are propagated immediately using the two\-phase commit protocol. If queued updating is used, the changes are stored in a queue; the queued transactions are then applied asynchronously at the Publisher whenever network connectivity is available. Because the updates are propagated asynchronously to the Publisher, the same data may have been updated by the Publisher or by another Subscriber and conflicts can occur when applying the updates. Conflicts are detected and resolved according to a conflict resolution policy that is set when creating the publication.  
  
 If you create a transactional publication with updatable subscriptions in the New Publication Wizard, both immediate updating and queued updating are enabled. If you create a publication with stored procedures, you can enable one or both options. When you create a subscription to the publication, you specify which update mode to use. You can then switch between update modes if necessary. For more information, see the following section "Switching between Update Modes".  
  
 To enable updatable subscriptions for transactional publications, [Enable Updating Subscriptions for Transactional Publications](../../Topics\TopicNameNotContainA/Enable-Updating-Subscriptions-for-Transactional-Publications.md)  
  
 To create updatable subscriptions for transactional publications, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md)  
  
## Switching Between Update Modes  
 When using updatable subscriptions you can specify that a subscription should use one update mode and then switch to the other if the application requires it. For example, you can specify that a subscription should use immediate updating, but switch to queued updating if a system failure results in the loss of network connectivity.  
  
> [!NOTE]  
>  Replication does not switch automatically between update modes. You must set the update mode through SQL Server Management Studio or your application must call [sp_setreplfailovermode &#40;Transact-SQL&#41;](../Topic/sp_setreplfailovermode%20\(Transact-SQL\).md) to switch between modes.  
  
 If you switch from immediate updating to queued updating, you cannot switch back to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.  
  
 **To switch between update modes**  
  
 To switch between updating modes, you must enable the publication and subscription for both update modes, and then switch between them if necessary. For more information, see  
[Switch Between Update Modes for an Updatable Transactional Subscription](../../Topics\TopicNameNotContainA/Switch-Between-Update-Modes-for-an-Updatable-Transactional-Subscription.md).  
  
### Considerations for Using Updatable Subscriptions  
  
-   After a publication is enabled for updating subscriptions or queued updating subscriptions, the option cannot be disabled for the publication \(although subscriptions do not need to use it\). To disable the option, the publication must be deleted and a new one created.  
  
-   Republishing data is not supported.  
  
-   Replication adds the **msrepl\_tran\_version** column to published tables for tracking purposes. Because of this additional column, all **INSERT** statements should include a column list.  
  
-   To make schema changes on a table in a publication that supports updating subscriptions, all activity on the table must be stopped at the Publisher and Subscribers, and pending data changes must be propagated to all nodes before making any schema changes. This ensures that outstanding transactions do not conflict with the pending schema change. After the schema changes have propagated to all nodes, activity can resume on the published tables. For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Quiesce%20a%20Replication%20Topology%20\(Replication%20Transact-SQL%20Programming\).md).  
  
-   If you plan to switch between update modes, the Queue Reader Agent must run at least once after the subscription has been initialized \(by default, the Queue Reader Agent runs continuously\).  
  
-   If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber, but not at the Publisher, the Subscriber cannot update the preexisting rows. Attempting to update these rows returns an error. The rows should be deleted from the table and then added at the Publisher.  
  
### Updates at the Subscriber  
  
-   Updates at the Subscriber are propagated to the Publisher even if a subscription is expired or is inactive. Ensure that any such subscriptions are either dropped or reinitialized.  
  
-   If **TIMESTAMP** or **IDENTITY** columns are used, and they are replicated as their base data types, values in these columns should not be updated at the Subscriber.  
  
-   Subscribers cannot update or insert **text**, **ntext** or **image** values because it is not possible to read from the inserted or deleted tables inside the replication change\-tracking triggers. Similarly, Subscribers cannot update or insert **text** or **image** values using **WRITETEXT** or **UPDATETEXT** because the data is overwritten by the Publisher. Instead, you could partition the **text** and **image** columns into a separate table and modify the two tables within a transaction.  
  
     To update large objects at a Subscriber, use the data types **varchar\(max\)**, **nvarchar\(max\)**, **varbinary\(max\)** instead of **text**, **ntext**, and **image** data types, respectively.  
  
-   Updates to unique keys \(including primary keys\) that generate duplicates \(for example, an update of the form `UPDATE <column> SET <column> =<column>+1` are not allowed and will be rejected because of a uniqueness violation. This is because set updates made at the Subscriber are propagated by replication as individual **UPDATE** statements for each row affected.  
  
-   If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber but not at the Publisher, the Subscriber cannot update the pre\-existing rows. Attempting to update these rows returns an error. The rows should be deleted from the table and inserted again.  
  
### User\-defined Triggers  
  
-   If the application requires triggers at the Subscriber, the triggers should be defined with the `NOT FOR REPLICATION` option at the Publisher and Subscriber. This ensures that triggers fire only for the original data change, but not when that change is replicated.  
  
     Ensure that the user\-defined trigger does not fire when the replication trigger updates the table. This is accomplished by calling the procedure **sp\_check\_for\_sync\_trigger** in the body of the user\-defined trigger. For more information, see [sp_check_for_sync_trigger &#40;Transact-SQL&#41;](../Topic/sp_check_for_sync_trigger%20\(Transact-SQL\).md).  
  
### Immediate Updating  
  
-   For immediate updating subscriptions, changes at the Subscriber are propagated to the Publisher and applied using Microsoft Distributed Transaction Coordinator \(MS DTC\). Ensure that MS DTC is installed and configured at the Publisher and Subscriber. For more information, see the Windows documentation.  
  
-   The triggers used by immediate updating subscriptions require a connection to the Publisher to replicate changes.  
  
-   If the publication allows immediate updating subscriptions and an article in the publication has a column filter, you cannot filter out non\-nullable columns without defaults.  
  
### Queued Updating  
  
-   Tables included in a merge publication cannot also be published as part of a transactional publication that allows queued updating subscriptions.  
  
-   Updates made to primary key columns are not recommended when using queued updating because the primary key is used as a record locator for all queries. When the conflict resolution policy is set to Subscriber Wins, updates to primary keys should be made with caution. If updates to the primary key are made at both the Publisher and at the Subscriber, the result will be two rows with different primary keys.  
  
-   For columns of data type **SQL\_VARIANT**: when data is inserted or updated at the Subscriber, it is mapped in the following way by the Queue Reader Agent when it is copied from the Subscriber to the queue:  
  
    -   **BIGINT**, **DECIMAL**, **NUMERIC**, **MONEY**, and **SMALLMONEY** are mapped to **NUMERIC**.  
  
    -   **BINARY** and **VARBINARY** are mapped to **VARBINARY** data.  
  
### Conflict Detection and Resolution  
  
-   For the Subscriber Wins conflict policy: conflict resolution is not supported for updates to primary key columns.  
  
-   Conflicts due to foreign key constraint failures are not resolved by replication:  
  
    -   If conflicts are not expected and data is well partitioned \(Subscribers do not update the same rows\), you can use foreign key constraints on the Publisher and Subscribers.  
  
    -   If conflicts are expected: you should not use foreign key constraints at the Publisher or Subscriber if you use "Subscriber wins" conflict resolution; you should not use foreign key constraints at the Subscriber if you use "Publisher wins" conflict resolution.  
  
## See Also  
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)   
 [Publication Types for Transactional Replication](../../Topics\TopicNameNotContainA/Publication-Types-for-Transactional-Replication.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  