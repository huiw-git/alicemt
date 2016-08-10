---
title: "Initialize a Subscription Manually"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Initialize a Subscription Manually
This topic describes how to initialize a subscription manually in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. While the initial snapshot is normally used to initialize a subscription, subscriptions to publications can be initialized without using a snapshot, provided that the schema and initial data are already present at the subscriber.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   **To initialize a subscription manually, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If there is activity on a database published using transactional replication between the time data and schema are copied to the Subscriber and the time at which the subscription is manually initialized, changes resulting from this activity might not be replicated to the Subscriber.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Initialize a subscription to a publication manually by copying the schema (and typically data) to the subscription database. The schema and data should match the publication database. Then specify that the subscription does not require schema and data on the **Initialize Subscriptions** page of the New Subscription Wizard. For more information about accessing this wizard, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md) and [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
 When you synchronize the subscription for the first time, the objects and metadata required by replication are copied to the subscription database.  
  
#### To initialize a subscription to a publication manually  
  
1.  Ensure that the schema and data are copied to the subscription database.  
  
2.  Clear the **Initialize** check box on the **Initialize Subscriptions** page of the New Subscription Wizard. Do this for each subscription that requires only replication objects and metadata to be copied.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 Subscriptions can be initialized manually using replication stored procedures.  
  
#### To manually initialize a pull subscription to a transactional publication  
  
1.  Ensure that the schema and data exist on the subscription database. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
2.  At the Publisher on the publication database, execute [sp_addsubscription](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0). Specify **@publication**, **@subscriber**, the name of the database at the Subscriber containing the published data for **@destination_db**, a value of **pull** for **@subscription_type**, and a value of **replication support only** for **@sync_type**. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
3.  At the Subscriber, execute [sp_addpullsubscription](assetId:///0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f). For updating subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics/TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
4.  At the Subscriber, execute [sp_addpullsubscription_agent](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
5.  Start the Distribution Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Pull Subscription](../../Topics/TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
#### To manually initialize a push subscription to a transactional publication  
  
1.  Ensure that the schema and data exist on the subscription database. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
2.  At the Publisher on the publication database, execute [sp_addsubscription](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0). Specify the name of the database at the Subscriber containing the published data for **@destination_db**, a value of **push** for **@subscription_type**, and a value of **replication support only** for **@sync_type**. For updating subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics/TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
3.  At the Publisher on the publication database, execute [sp_addpushsubscription_agent](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b). For more information, see [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md).  
  
4.  Start the Distribution Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Push Subscription](../../Topics/TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
#### To manually initialize a pull subscription to a merge publication  
  
1.  Ensure that the schema and data exist on the subscription database. This can be done by restoring a backup of the publication database at the Subscriber.  
  
2.  At the Publisher, execute [sp_addmergesubscription](assetId:///a191d817-0132-49ff-93ca-76f13e609b38). Specify **@publication**, **@subscriber**, **@subscriber_db**, and a value of **pull** for **@subscription_type**. This registers the pull subscription.  
  
3.  At the Subscriber on the database containing the published data, execute [sp_addmergepullsubscription](assetId:///d63909a0-8ea7-4734-9ce8-8204d936a3e4). Specify a value of **none** for **@sync_type**.  
  
4.  At the Subscriber, execute [sp_addmergepullsubscription_agent](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
5.  Start the Merge Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Pull Subscription](../../Topics/TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
#### To manually initialize a push subscription to a merge publication  
  
1.  Ensure that the schema and data exist on the subscription database. This can be done by restoring a backup of the publication database at the Subscriber.  
  
2.  At the Publisher on the publication database, execute [sp_addmergesubscription](assetId:///a191d817-0132-49ff-93ca-76f13e609b38). Specify the name of the database at the Subscriber containing the published data for **@subscriber_db**, a value of **push** for **@subscription_type**, and a value of **none** for **@sync_type**.  
  
3.  At the Publisher on the publication database, execute [sp_addmergepushsubscription_agent](assetId:///808a1925-be46-4999-8d69-b3a83010ec81). For more information, see [Create a Push Subscription](../../Topics/TopicNameContainA/Create-a-Push-Subscription.md).  
  
4.  Start the Merge Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Push Subscription](../../Topics/TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
## See Also  
 [Initialize a Transactional Subscription Without a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md)   
 [Back Up and Restore Replicated Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [Replication Security Best Practices](../../Topics/TopicNameNotContainA/Replication-Security-Best-Practices.md)