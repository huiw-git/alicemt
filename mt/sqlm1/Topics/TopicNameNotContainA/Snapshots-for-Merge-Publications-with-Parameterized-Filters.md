---
title: Snapshots for Merge Publications with Parameterized Filters
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99d7ae15-5457-4ad4-886b-19c17371f72c
---
# Snapshots for Merge Publications with Parameterized Filters
  When parameterized row filters are used in merge publications, replication initializes each subscription with a two\-part snapshot. First, a schema snapshot is created that contains all objects required by replication and the schema of the published objects, but not the data. Then, each subscription is initialized with a snapshot that includes the objects and schema from the schema snapshot and the data that belongs to the subscription's partition. If more than one subscription receives a given partition \(in other words, they receive the same schema and data\), the snapshot for that partition is created only once; multiple subscriptions are initialized from the same snapshot. For more information about parameterized row filters, see [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
 You can create snapshots for publications with parameterized filters in one of three ways:  
  
-   Pre\-generate snapshots for each partition. Using this option allows you to control when snapshots are generated.  
  
     You can also choose to have the snapshots refreshed on a schedule. New Subscribers that subscribe to a partition for which a snapshot has been created will receive an up\-to\-date snapshot.  
  
-   Allow Subscribers to request snapshot generation and application the first time they synchronize. Using this option allows new Subscribers to synchronize without requiring intervention from an administrator \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent must be running at the Publisher to allow the snapshot to be generated\).  
  
    > [!NOTE]  
    >  If the filtering for one or more articles in the publication yields non\-overlapping partitions that are unique for each subscription, metadata is cleaned up whenever the Merge Agent runs. This means that the partitioned snapshot expires more quickly. When using this option, you should consider allowing Subscribers to initiate snapshot generation and delivery. For more information about filtering options, see [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
-   Manually generate a snapshot for each Subscriber with the Snapshot Agent. The Subscriber must then provide the snapshot location to the Merge Agent, so it can retrieve and apply the correct snapshot.  
  
    > [!NOTE]  
    >  This option is supported for backward compatibility and does not allow FTP snapshot shares.  
  
 The most flexible approach is to use a combination of pre\-generated and Subscriber\-requested snapshot options: snapshots are pre\-generated and refreshed on a scheduled basis \(usually during off\-peak times\), but a Subscriber can generate its own snapshot if a subscription that requires a new partition is created.  
  
 Consider [!INCLUDE[ssSampleDBCoShort](../../Token\Other/ssSampleDBCoShort_md.md)], which has a mobile work force that delivers inventory to individual stores. Each sales person receives a subscription based on their login, which retrieves the data for the stores they service. The administrator chooses to pre\-generate snapshots and refresh them every Sunday. Occasionally a new user is added to the system and needs data for a partition that does not have a snapshot available. The administrator also chooses to allow Subscriber\-initiated snapshots to avoid the situation where a Subscriber cannot subscribe to the publication because the snapshot is not yet available. When the new Subscriber connects for the first time, the snapshot is generated for the specified partition and applied at the Subscriber \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent must be running at the Publisher to allow the snapshot to be generated\).  
  
 To create a snapshot for a publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../../Topics\TopicNameContainA/Create-a-Snapshot-for-a-Merge-Publication-with-Parameterized-Filters.md).  
  
## Security Settings for the Snapshot Agent  
 The Snapshot Agent creates snapshots for each partition. For pre\-generated snapshots and snapshots requested by a Subscriber, the agent runs and makes connections under the credentials that were specified when the snapshot agent job for the publication was created \(the job is created by the New Publication Wizard or **sp\_addpublication\_snapshot**\). To change the credentials, use **sp\_changedynamicsnapshot\_job**. For more information, see [sp_changedynamicsnapshot_job &#40;Transact-SQL&#41;](../Topic/sp_changedynamicsnapshot_job%20\(Transact-SQL\).md).  
  
## See Also  
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md)   
 [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md)  
  
  