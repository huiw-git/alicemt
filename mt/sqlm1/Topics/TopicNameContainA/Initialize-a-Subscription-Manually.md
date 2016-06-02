---
title: Initialize a Subscription Manually
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
---
# Initialize a Subscription Manually
  This topic describes how to initialize a subscription manually in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. While the initial snapshot is normally used to initialize a subscription, subscriptions to publications can be initialized without using a snapshot, provided that the schema and initial data are already present at the subscriber.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   **To initialize a subscription manually, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If there is activity on a database published using transactional replication between the time data and schema are copied to the Subscriber and the time at which the subscription is manually initialized, changes resulting from this activity might not be replicated to the Subscriber.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Initialize a subscription to a publication manually by copying the schema \(and typically data\) to the subscription database. The schema and data should match the publication database. Then specify that the subscription does not require schema and data on the **Initialize Subscriptions** page of the New Subscription Wizard. For more information about accessing this wizard, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md) and [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
 When you synchronize the subscription for the first time, the objects and metadata required by replication are copied to the subscription database.  
  
#### To initialize a subscription to a publication manually  
  
1.  Ensure that the schema and data are copied to the subscription database.  
  
2.  Clear the **Initialize** check box on the **Initialize Subscriptions** page of the New Subscription Wizard. Do this for each subscription that requires only replication objects and metadata to be copied.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Subscriptions can be initialized manually using replication stored procedures.  
  
#### To manually initialize a pull subscription to a transactional publication  
  
1.  Ensure that the schema and data exist on the subscription database. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
2.  At the Publisher on the publication database, execute [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, the name of the database at the Subscriber containing the published data for **@destination\_db**, a value of **pull** for **@subscription\_type**, and a value of **replication support only** for **@sync\_type**. For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
3.  At the Subscriber, execute [sp\_addpullsubscription](../Topic/sp_addpullsubscription%20\(Transact-SQL\).md). For updating subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
4.  At the Subscriber, execute [sp\_addpullsubscription\_agent](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
5.  Start the Distribution Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
#### To manually initialize a push subscription to a transactional publication  
  
1.  Ensure that the schema and data exist on the subscription database. For more information, see [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md).  
  
2.  At the Publisher on the publication database, execute [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md). Specify the name of the database at the Subscriber containing the published data for **@destination\_db**, a value of **push** for **@subscription\_type**, and a value of **replication support only** for **@sync\_type**. For updating subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
3.  At the Publisher on the publication database, execute [sp\_addpushsubscription\_agent](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md). For more information, see [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
4.  Start the Distribution Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
#### To manually initialize a pull subscription to a merge publication  
  
1.  Ensure that the schema and data exist on the subscription database. This can be done by restoring a backup of the publication database at the Subscriber.  
  
2.  At the Publisher, execute [sp\_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, **@subscriber\_db**, and a value of **pull** for **@subscription\_type**. This registers the pull subscription.  
  
3.  At the Subscriber on the database containing the published data, execute [sp\_addmergepullsubscription](../Topic/sp_addmergepullsubscription%20\(Transact-SQL\).md). Specify a value of **none** for **@sync\_type**.  
  
4.  At the Subscriber, execute [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
5.  Start the Merge Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
#### To manually initialize a push subscription to a merge publication  
  
1.  Ensure that the schema and data exist on the subscription database. This can be done by restoring a backup of the publication database at the Subscriber.  
  
2.  At the Publisher on the publication database, execute [sp\_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md). Specify the name of the database at the Subscriber containing the published data for **@subscriber\_db**, a value of **push** for **@subscription\_type**, and a value of **none** for **@sync\_type**.  
  
3.  At the Publisher on the publication database, execute [sp\_addmergepushsubscription\_agent](../Topic/sp_addmergepushsubscription_agent%20\(Transact-SQL\).md). For more information, see [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
4.  Start the Merge Agent to transfer replication objects and download the latest changes from the Publisher. For more information, see [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md).  
  
## See Also  
 [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md)   
 [Back Up and Restore Replicated Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  