---
title: Delete a Pull Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
---
# Delete a Pull Subscription
  This topic describes how to delete a pull subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To delete a pull subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Delete a pull subscription at the Publisher \(from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]\) or the Subscriber \(from the **Local Subscriptions** folder\). Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.  
  
#### To delete a pull subscription at the Publisher  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Expand the publication associated with the subscription you want to delete.  
  
4.  Right\-click the subscription, and then click **Delete**.  
  
5.  In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information. If you clear the **Connect to Subscriber** check box, you should connect to the Subscriber later to delete the information.  
  
#### To delete a pull subscription at the Subscriber  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.  
  
3.  Right\-click the subscription you want to delete, and then click **Delete**.  
  
4.  In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information. If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Pull subscriptions can be deleted programmatically using replication stored procedures. The stored procedures used will depend on the type of publication to which the subscription belongs.  
  
#### To delete a pull subscription to a snapshot or transactional publication  
  
1.  At the Subscriber on the subscription database, execute [sp_droppullsubscription &#40;Transact-SQL&#41;](../Topic/sp_droppullsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@publisher**, and **@publisher\_db**.  
  
2.  At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](../Topic/sp_dropsubscription%20\(Transact-SQL\).md). Specify **@publication** and **@subscriber**. Specify a value of **all** for **@article**. \(Optional\) If the Distributor cannot be accessed, specify a value of **1** for **@ignore\_distributor** to delete the subscription without removing related objects at the Distributor.  
  
#### To delete a pull subscription to a merge publication  
  
1.  At the Subscriber on the subscription database, execute [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../Topic/sp_dropmergepullsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@publisher**, and **@publisher\_db**.  
  
2.  At the Publisher on the publication database, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](../Topic/sp_dropmergesubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, and **@subscriber\_db**. Specify a value of **pull** for **@subscription\_type**. \(Optional\) If the Distributor cannot be accessed, specify a value of **1** for **@ignore\_distributor** to delete the subscription without removing related objects at the Distributor.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 The following example deletes a pull subscription to a transactional publication. The first batch is executed at the Subscriber and the second is executed at the Publisher.  
  
 [!CODE [HowTo#sp_droptranpullsubscription](../CodeSnippet/SQL15/replication/howto#sp_droptranpullsubscription)]  
  
 [!CODE [HowTo#sp_droptransubscription](../CodeSnippet/SQL15/replication/howto#sp_droptransubscription)]  
  
 The following example deletes a pull subscription to a merge publication. The first batch is executed at the Subscriber and the second is executed at the Publisher.  
  
 [!CODE [HowTo#sp_dropmergepullsubscription](../CodeSnippet/SQL15/replication/howto#sp_dropmergepullsubscription)]  
  
 [!CODE [HowTo#sp_dropmergesubscription](../CodeSnippet/SQL15/replication/howto#sp_dropmergesubscription)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can delete pull subscriptions programmatically by using Replication Management Objects \(RMO\). The RMO classes that you use to delete a pull subscription depend on the type of publication to which the pull subscription is subscribed.  
  
#### To delete a pull subscription to a snapshot or transactional publication  
  
1.  Create connections to both the Subscriber and Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) Class.  
  
2.  Create an instance of the [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) class, and set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName), and [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName) properties. Use the Subscriber connection from step 1 to set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
3.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the subscription exists. If the value of this property is **false**, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.  
  
4.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.PullSubscription.Remove) method.  
  
5.  Create an instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
6.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 5 are incorrect or the publication does not exist on the server.  
  
7.  Call the [RemovePullSubscription](assetId:///M:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription(System.String,System.String)) method. Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.  
  
#### To delete a pull subscription to a merge publication  
  
1.  Create connections to both the Subscriber and Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) Class.  
  
2.  Create an instance of the [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) class, and set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName), and [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName) properties. Use the connection from step 1 to set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
3.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the subscription exists. If the value of this property is **false**, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.  
  
4.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.PullSubscription.Remove) method.  
  
5.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
6.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 5 are incorrect or the publication does not exist on the server.  
  
7.  Call the [RemovePullSubscription](assetId:///M:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription(System.String,System.String)) method. Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example deletes a pull subscription to a transactional publication and removes the subscription registration at the Publisher.  
  
 [!CODE [HowTo#rmo_DropTranPullSub](../CodeSnippet/SQL15/replication/howto#rmo_droptranpullsub)]  
  
 [!CODE [HowTo#rmo_vb_DropTranPullSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_droptranpullsub)]  
  
 This example deletes a pull subscription to a merge publication and removes the subscription registration at the Publisher.  
  
 [!CODE [HowTo#rmo_DropMergePullSub](../CodeSnippet/SQL15/replication/howto#rmo_dropmergepullsub)]  
  
 [!CODE [HowTo#rmo_vb_DropMergePullSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_dropmergepullsub)]  
  
## See Also  
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  