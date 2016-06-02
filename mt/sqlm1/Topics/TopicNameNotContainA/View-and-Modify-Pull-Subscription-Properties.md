---
title: View and Modify Pull Subscription Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
---
# View and Modify Pull Subscription Properties
  This topic describes how to view and modify pull subscription properties in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To view and modify pull subscription properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 View pull subscription properties from the Publisher or the Subscriber in the **Subscription Properties \- \<Publisher\>: \<PublicationDatabase\>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. More properties are visible from the Subscriber, and properties can be modified at the Subscriber. You can also view properties from the Publisher on the **All Subscriptions** tab, which is available in Replication Monitor. For information about starting Replication Monitor, see [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md).  
  
#### To view pull subscription properties from the Publisher in Management Studio  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Expand the appropriate publication, right\-click a subscription, and then click **Properties**.  
  
4.  View properties, and then click **OK**.  
  
#### To view and modify pull subscription properties from the Subscriber in Management Studio  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.  
  
3.  Right\-click a subscription, and then click **Properties**.  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
#### To view pull subscription properties from the Publisher in Replication Monitor  
  
1.  Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.  
  
2.  Click the **All Subscriptions** tab.  
  
3.  Right\-click a subscription, and then click **Properties**.  
  
4.  View properties, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Pull subscriptions can be modified and their properties accessed programmatically using replication stored procedures. The stored procedures used depend on the type of publication to which the subscription belongs.  
  
#### To view the properties of a pull subscription to a snapshot or transactional publication  
  
1.  At the Subscriber, execute [sp\_helppullsubscription](../Topic/sp_helppullsubscription%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, and **@publication**. This returns information about the subscription that is stored in system tables at the Subscriber.  
  
2.  At the Subscriber, execute [sp\_helpsubscription\_properties](../Topic/sp_helpsubscription_properties%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, **@publication**, and one of the following values for **@publication\_type**:  
  
    -   **0** \- Subscription belongs to a transactional publication.  
  
    -   **1** \- Subscription belongs to a snapshot publication.  
  
3.  At the Publisher, execute [sp\_helpsubscription](../Topic/sp_helpsubscription%20\(Transact-SQL\).md). Specify **@publication** and **@subscriber**.  
  
4.  At the Publisher, execute [sp\_helpsubscriberinfo](../Topic/sp_helpsubscriberinfo%20\(Transact-SQL\).md), specifying **@subscriber**. This displays information about the Subscriber.  
  
#### To change the properties of a pull subscription to a snapshot or transactional publication  
  
1.  At the Subscriber, execute [sp\_change\_subscription\_properties](../Topic/sp_change_subscription_properties%20\(Transact-SQL\).md), specifying **@publisher**, **@publisher\_db**, **@publication**, a value of either **0** \(transactional\) or **1** \(snapshot\) for **@publication\_type**, the subscription property being changed as **@property**, and the new value as **@value**.  
  
2.  \(Optional\) At the Subscriber on the subscription database, execute [sp\_changesubscriptiondtsinfo](../Topic/sp_changesubscriptiondtsinfo%20\(Transact-SQL\).md). Specify the ID of the Distribution Agent job for **@jobid**, and the following Data Transformation Services \(DTS\) package properties:  
  
    -   **@dts\_package\_name**  
  
    -   **@dts\_package\_password**  
  
    -   **@dts\_package\_location**  
  
     This changes the DTS package properties of a subscription.  
  
    > [!NOTE]  
    >  The job ID can be obtained by executing [sp\_helpsubscription](../Topic/sp_helpsubscription%20\(Transact-SQL\).md).  
  
#### To view the properties of a pull subscription to a merge publication  
  
1.  At the Subscriber, execute [sp\_helpmergepullsubscription](../Topic/sp_helpmergepullsubscription%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, and **@publication**.  
  
2.  At the Subscriber, execute [sp\_helpsubscription\_properties](../Topic/sp_helpsubscription_properties%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, **@publication**, and a value of 2 for **@publication\_type**.  
  
3.  At the Publisher, execute [sp\_helpmergesubscription](../Topic/sp_helpmergesubscription%20\(Transact-SQL\).md) to display subscription information. To return information on a specific subscription, you must specify **@publication**, **@subscriber**, and a value of **pull** for **@subscription\_type**.  
  
4.  At the Publisher, execute [sp\_helpsubscriberinfo](../Topic/sp_helpsubscriberinfo%20\(Transact-SQL\).md), specifying **@subscriber**. This displays information about the Subscriber.  
  
#### To change the properties of a pull subscription to a merge publication  
  
1.  At the Subscriber, execute [sp\_changemergepullsubscription](../Topic/sp_changemergepullsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@publisher**, **@publisher\_db**, the subscription property being changed as **@property**, and the new value as **@value**.  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 The RMO classes you use to view or modify pull subscription properties depend on the type of publication to which the pull subscription is subscribed.  
  
#### To view or modify properties of a pull subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName), and [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName) properties.  
  
4.  Set the connection from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.  
  
6.  \(Optional\) To change properties, set a new value for one of the [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) properties that can be set, and then call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  \(Optional\) To view the new settings, call the [Refresh](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Refresh) method to reload the properties for the article.  
  
8.  Close all connections.  
  
#### To view or modify properties of a pull subscription to a merge publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName), and [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName) properties.  
  
4.  Set the connection from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.  
  
6.  \(Optional\) To change properties, set a new value for one of the [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) properties that can be set, and then call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  \(Optional\) To view the new settings, call the [Refresh](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Refresh) method to reload the properties for the article.  
  
8.  Close all connections.  
  
## See Also  
 [View Information and Perform Tasks for a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Subscription%20\(Replication%20Monitor\).md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  