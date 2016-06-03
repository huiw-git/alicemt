---
title: Delete a Push Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
---
# Delete a Push Subscription
  This topic describes how to delete a push subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To delete a push subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Delete a push subscription at the Publisher \(from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]\) or the Subscriber \(from the **Local Subscriptions** folder\). Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.  
  
#### To delete a push subscription at the Publisher  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Expand the publication associated with the subscription you want to delete.  
  
4.  Right\-click the subscription, and then click **Delete**.  
  
5.  In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information. If you clear the **Connect to Subscriber** checkbox, you should connect to the Subscriber later to delete the information.  
  
#### To delete a push subscription at the Subscriber  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.  
  
3.  Right\-click the subscription you want to delete, and then click **Delete**.  
  
4.  In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information. If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Push subscriptions can be deleted programmatically using replication stored procedures. The stored procedures used depend on the type of publication to which the subscription belongs.  
  
#### To delete a push subscription to a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](../Topic/sp_dropsubscription%20\(Transact-SQL\).md). Specify **@publication** and **@subscriber**. Specify a value of **all** for **@article**. \(Optional\) If the Distributor cannot be accessed, specify a value of **1** for **@ignore\_distributor** to delete the subscription without removing related objects at the Distributor.  
  
2.  At the Subscriber on the subscription database, execute [sp_subscription_cleanup &#40;Transact-SQL&#41;](../Topic/sp_subscription_cleanup%20\(Transact-SQL\).md) to remove replication metadata in the subscription database.  
  
#### To delete a push subscription to a merge publication  
  
1.  At the Publisher, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](../Topic/sp_dropmergesubscription%20\(Transact-SQL\).md), specifying **@publication**, **@subscriber** and **@subscriber\_db**. \(Optional\) If the Distributor cannot be accessed, specify a value of **1** for **@ignore\_distributor** to delete the subscription without removing related objects at the Distributor.  
  
2.  At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../Topic/sp_mergesubscription_cleanup%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, and **@publication**. This removes merge metadata from the subscription database.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example deletes a push subscription to a transactional publication.  
  
 [!CODE [HowTo#sp_droptransubscription](../CodeSnippet/SQL15/replication/howto#sp_droptransubscription)]  
  
 This example deletes a push subscription to a merge publication.  
  
 [!CODE [HowTo#sp_dropmergesubscription](../CodeSnippet/SQL15/replication/howto#sp_dropmergesubscription)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 The RMO classes that you use to delete a push subscription depend on the type of publication to which the push subscription is subscribed.  
  
#### To delete a push subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName), [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName), [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName), and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName) properties.  
  
4.  Set the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the subscription exists. If the value of this property is **false**, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.  
  
6.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Remove) method.  
  
#### To delete a push subscription to a merge publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName), [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName), [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName), and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName) properties.  
  
4.  Set the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the subscription exists. If the value of this property is **false**, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.  
  
6.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Remove) method.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 You can delete push subscriptions programmatically by using Replication Management Objects \(RMO\).  
  
 [!CODE [HowTo#rmo_DropTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_droptranpushsub)]  
  
 [!CODE [HowTo#rmo_vb_DropTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_droptranpushsub)]  
  
## See Also  
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  