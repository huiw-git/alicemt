---
title: View and Modify Push Subscription Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
---
# View and Modify Push Subscription Properties
  This topic describes how to view and modify push subscription properties in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To view and modify push subscription properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 View and modify push subscription properties from the Publisher in:  
  
-   The **Subscription Properties \- \<Publisher\>: \<PublicationDatabase\>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
-   The **All Subscriptions** tab, which is available in Replication Monitor. For information about starting Replication Monitor, see [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md).  
  
#### To view and modify push subscription properties in Management Studio  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Expand the appropriate publication, right\-click a subscription, and then click **Properties**.  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
#### To view and modify push subscription properties in Replication Monitor  
  
1.  Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.  
  
2.  Click the **All Subscriptions** tab.  
  
3.  Right\-click a subscription, and then click **Properties**.  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Push subscriptions can be modified and their properties accessed programmatically using replication stored procedures. The stored procedures used depend on the type of publication to which the subscription belongs.  
  
#### To view the properties of a push subscription to a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_helpsubscription](../Topic/sp_helpsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, and a value of **all** for **@article**.  
  
2.  At the Publisher on the publication database, execute [sp\_helpsubscriberinfo](../Topic/sp_helpsubscriberinfo%20\(Transact-SQL\).md), specifying **@subscriber**.  
  
#### To change the properties of a push subscription to a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_changesubscriber](../Topic/sp_changesubscriber%20\(Transact-SQL\).md), specifying **@subscriber** and any parameters for the Subscriber properties being changed.  
  
2.  At the Publisher on the publication database, execute [sp\_changesubscription](../Topic/sp_changesubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, **@destination\_db**, a value of **all** for **@article**, the subscription property being changed as **@property**, and the new value as **@value**. This changes security settings for the push subscription.  
  
3.  \(Optional\) To change the Data Transformation Services \(DTS\) package properties of a subscription, execute [sp\_changesubscriptiondtsinfo](../Topic/sp_changesubscriptiondtsinfo%20\(Transact-SQL\).md) at the Subscriber on the subscription database. Specify the ID of the Distribution Agent job for **@jobid** and the following DTS package properties:  
  
    -   **@dts\_package\_name**  
  
    -   **@dts\_package\_password**  
  
    -   **@dts\_package\_location**  
  
     This changes the DTS package properties of a subscription.  
  
    > [!NOTE]  
    >  The job ID can be obtained by executing [sp\_helpsubscription](../Topic/sp_helpsubscription%20\(Transact-SQL\).md).  
  
#### To view the properties of a push subscription to a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_helpmergesubscription](../Topic/sp_helpmergesubscription%20\(Transact-SQL\).md). Specify **@publication** and **@subscriber**.  
  
2.  At the Publisher, execute [sp\_helpsubscriberinfo](../Topic/sp_helpsubscriberinfo%20\(Transact-SQL\).md), specifying **@subscriber**.  
  
#### To change the properties of a push subscription to a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_changemergesubscription](../Topic/sp_changemergesubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, **@subscriber\_db**, the subscription property being changed as **@property**, and the new value as **@value**.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 The RMO classes you use to view or modify push subscription properties depend on the type of publication to which the push subscription is subscribed.  
  
#### To view or modify properties of a push subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName), [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName), and [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName) properties.  
  
4.  Set the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property setting.  
  
5.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.  
  
6.  \(Optional\) To change properties, set a new value for one of the [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) properties that can be set, and then call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  \(Optional\) To view the new settings, call the [Refresh](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Refresh) method to reload the properties for the subscription.  
  
#### To view or modify properties of a push subscription to a merge publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) class.  
  
3.  Set the [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName), [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName), and [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName) properties.  
  
4.  Set the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property setting.  
  
5.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.  
  
6.  \(Optional\) To change properties, set a new value for one of the [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) properties that can be set, and then call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  \(Optional\) To view the new settings, call the [Refresh](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Refresh) method to reload the properties for the subscription.  
  
## See Also  
 [View Information and Perform Tasks for a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Subscription%20\(Replication%20Monitor\).md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  