---
title: Initialize Subscriptions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
---
# Initialize Subscriptions
  Subscribers must be initialized before they can begin receiving replicated data. An initial dataset is not required, but the Subscriber must at least have the schema for each replicated object and any metadata tables and procedures required by replication.  
  
## Options  
 **Subscription properties**  
 Select the check box in the **Initialize** column for each Subscriber that requires an initial data set. If the check box is cleared, only the replication metadata and procedures will be initialized. For more information about initializing a subscription without a snapshot, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
 Select **Immediately** from the drop\-down list box in the **Initialize When** column to have the Merge Agent or Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed. Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run. The **Immediately** option is not available for pull subscriptions to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)]. The Merge Agent and Distribution Agent do not run on instances of [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)]; therefore the subscription must be initialized through another method.  
  
> [!NOTE]  
>  The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.  
  
## See Also  
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)   
 [Initialize a Subscription](../../Topics\TopicNameContainA/Initialize-a-Subscription.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  