---
title: Subscribe to Publications
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
---
# Subscribe to Publications
  A subscription is a request for a copy of the data and database objects in a publication. A subscription defines which publication will be received, and where and when it will be received. When planning for subscriptions, consider where you want agent processing to occur. The type of subscription you choose controls where the agent runs. With a push subscription, the Merge Agent or Distribution Agent runs at the Distributor, whereas with a pull subscription, agents run at the Subscribers. After a subscription is created, it cannot be changed from one type to another.  
  
|Subscription|Characteristics|Use When|  
|------------------|---------------------|--------------|  
|Push Subscription|With a push subscription, the Publisher propagates changes to a Subscriber without a request from the Subscriber. Changes can be pushed to Subscribers on demand, continuously, or on a scheduled basis. The Distribution Agent or Merge Agent runs at the Distributor.|Data will typically be synchronized continuously or on a frequently recurring schedule.<br /><br /> Publications require near real\-time movement of data.<br /><br /> The higher processor overhead at the Distributor does not affect performance.<br /><br /> Most often used with snapshot and transactional replication.|  
|Pull Subscription|With a pull subscription, the Subscriber requests changes made at the Publisher. Pull subscriptions allow the user at the Subscriber to determine when the data changes are synchronized. The Distribution Agent or the Merge Agent runs at the Subscriber.|Data will typically be synchronized on demand or on a schedule rather than continuously.<br /><br /> The publication has a large number of Subscribers, and\/or it would be too resource\-intensive to run all the agents at the Distributor.<br /><br /> Subscribers are autonomous, disconnected, and\/or mobile. Subscribers will determine when they will connect and synchronize changes.<br /><br /> Most often used with merge replication.|  
  
## Merge Replication Subscription Types  
 All replication types allow push and pull subscriptions. Merge replication uses two additional terms to distinguish subscriptions: client subscriptions and server subscriptions. Both client and server subscription types can be used with push and pull subscriptions. Client subscriptions are appropriate for most Subscribers, whereas server subscriptions are typically used for Subscribers that republish data to other Subscribers. Subscription choice also affects conflict resolution.  
  
## Non\-SQL Server Subscribers  
 Oracle and IBM DB2 can subscribe to snapshot and transactional publications using push subscriptions. For more information, see [Non-SQL Server Subscribers](../../Topics\TopicNameNotContainA/Non-SQL-Server-Subscribers.md).  
  
## Creating Subscriptions  
 To create a subscription, you supply the following information:  
  
-   The name of the publication.  
  
-   The name of the Subscriber and the subscription database.  
  
-   Whether the Distribution Agent or Merge Agent runs at the Distributor or at the Subscriber.  
  
-   Whether the Distribution Agent or Merge Agent runs continuously, on a scheduled basis, or on demand only.  
  
-   Whether the Snapshot Agent should create an initial snapshot for the subscription and whether the Distribution Agent or Merge Agent should apply that snapshot at the Subscriber.  
  
-   Accounts under which the Distribution Agent or Merge Agent will run.  
  
-   For merge replication, the type of subscription: server or client.  
  
 **To create a push subscription**  
  
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)  
  
 **To view or modify push subscription properties**  
  
 [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)  
  
 **To delete a push subscription**  
  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [Delete a Push Subscription](../../Topics\TopicNameContainA/Delete-a-Push-Subscription.md)  
  
> [!NOTE]  
>  Deleting a subscription does not remove published objects from the Subscriber.  
  
 **To create a pull subscription**  
  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)  
  
 **To view or modify pull subscription properties**  
  
 [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)  
  
 **To delete a pull subscription**  
  
 [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md)  
  
## See Also  
 [Secure the Subscriber](../../Topics\TopicNameNotContainA/Secure-the-Subscriber.md)   
 [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md)  
  
  