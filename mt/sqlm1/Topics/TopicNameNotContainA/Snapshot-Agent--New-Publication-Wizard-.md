---
title: Snapshot Agent (New Publication Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
---
# Snapshot Agent (New Publication Wizard)
  The Snapshot Agent creates files containing the publication schema and data that are used to initialize new subscriptions. By default, the Snapshot Agent runs immediately after the publication is created in the New Publication Wizard. Subsequently, the agent runs according to a schedule you specify. Whether the agent creates new snapshot files each time it runs depends on the type of replication and options chosen. For more information, see [Create and Apply the Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Snapshot.md).  
  
 For merge publications that use parameterized filters, you must create a snapshot for each partition of data after the publication snapshot has completed. For more information, see [Snapshots for Merge Publications with Parameterized Filters](../../Topics\TopicNameNotContainA/Snapshots-for-Merge-Publications-with-Parameterized-Filters.md).  
  
## Options  
 **Create a snapshot immediately** \(merge replication\) or **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** \(transactional replication\)  
 Select this check box to create a snapshot immediately after the New Publication Wizard is completed. Clear this check box if you plan to change snapshot properties in the **Publication Properties** dialog box before generating a snapshot, or if you will initialize the Subscriber without a snapshot. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
> [!NOTE]  
>  The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.  
  
 **Schedule the Snapshot Agent to run at the following times**  
 Accept the default schedule for running the Snapshot Agent, or click **Change** to specify a schedule.  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md)   
 [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)   
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)  
  
  