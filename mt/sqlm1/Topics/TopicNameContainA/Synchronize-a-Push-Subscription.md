---
title: Synchronize a Push Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
---
# Synchronize a Push Subscription
  This topic describes how to synchronize a push subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [replication agents](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md), or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To synchronize a push subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Replication Agents](#ReplProg)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Subscriptions are synchronized by the Distribution Agent \(for snapshot and transactional replication\) or the Merge Agent \(for merge replication\). Agents can run continuously, run on demand, or run on a schedule. For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
 Synchronize a subscription on demand from the **Local Publications** and **Local Subscriptions** folders in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and the **All Subscriptions** tab in Replication Monitor. Subscriptions to Oracle publications cannot be synchronized on demand from the Subscriber. For information about starting Replication Monitor, see [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md).  
  
#### To synchronize a push subscription on demand in Management Studio \(at the Publisher\)  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Expand the publication for which you want to synchronize subscriptions.  
  
4.  Right\-click the subscription you want to synchronize, and then click **View Synchronization Status**.  
  
5.  In the **View Synchronization Status \- \<Subscriber\>:\<SubscriptionDatabase\>** dialog box, click **Start**. When synchronization is complete, the message **Synchronization completed** is displayed.  
  
6.  Click **Close**.  
  
#### To synchronize a push subscription on demand in Management Studio \(at the Subscriber\)  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.  
  
3.  Right\-click the subscription you want to synchronize, and then click **View Synchronization Status**.  
  
4.  A message is displayed about establishing a connection to the Distributor. Click **OK**.  
  
5.  In the **View Synchronization Status \- \<Subscriber\>:\<SubscriptionDatabase\>** dialog box, click **Start**. When synchronization is complete, the message **Synchronization completed** is displayed.  
  
6.  Click **Close**.  
  
#### To synchronize a push subscription on demand in Replication Monitor  
  
1.  In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.  
  
2.  Click the **All Subscriptions** tab.  
  
3.  Right\-click the subscription you want to synchronize, and then click **Start Synchronizing**.  
  
4.  To view synchronization progress, right\-click the subscription, and then click **View Details**.  
  
##  <a name="ReplProg"></a> Using Replication Agents  
 Push subscriptions can be synchronized programmatically and on\-demand by invoking the appropriate replication agent executable file from the command prompt. The replication agent executable file that is invoked will depend on the type of publication to which the push subscription belongs.  
  
#### To start the Distribution Agent to synchronize a push subscription to a transactional publication  
  
1.  From the command prompt or in a batch file at the Distributor, execute **distrib.exe**. Specify the following command\-line arguments:  
  
    -   **\-Publisher**  
  
    -   **\-PublisherDB**  
  
    -   **\-Distributor**  
  
    -   **\-Subscriber**  
  
    -   **\-SubscriberDB**  
  
    -   **\-SubscriptionType \= 0**  
  
     If you are using SQL Server Authentication, you must also specify the following arguments:  
  
    -   **\-DistributorLogin**  
  
    -   **\-DistributorPassword**  
  
    -   **\-DistributorSecurityMode \= 0**  
  
    -   **\-PublisherLogin**  
  
    -   **\-PublisherPassword**  
  
    -   **\-PublisherSecurityMode \= 0**  
  
    -   **\-SubscriberLogin**  
  
    -   **\-SubscriberPassword**  
  
    -   **\-SubscriberSecurityMode \= 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
#### To start the Merge Agent to synchronize a push subscription to a merge publication  
  
1.  From the command prompt or in a batch file at the Distributor, execute **replmerg.exe**. Specify the following command\-line arguments:  
  
    -   **\-Publisher**  
  
    -   **\-PublisherDB**  
  
    -   **\-Publication**  
  
    -   **\-Distributor**  
  
    -   **\-Subscriber**  
  
    -   **\-SubscriberDB**  
  
    -   **\-SubscriptionType \= 0**  
  
     If you are using SQL Server Authentication, you must also specify the following arguments:  
  
    -   **\-DistributorLogin**  
  
    -   **\-DistributorPassword**  
  
    -   **\-DistributorSecurityMode \= 0**  
  
    -   **\-PublisherLogin**  
  
    -   **\-PublisherPassword**  
  
    -   **\-PublisherSecurityMode \= 0**  
  
    -   **\-SubscriberLogin**  
  
    -   **\-SubscriberPassword**  
  
    -   **\-SubscriberSecurityMode \= 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../Token\Other/ssNoteWinAuthentication_md.md)]  
  
###  <a name="TsqlExample"></a> Examples \(Replication Agents\)  
 The following example starts the Distribution Agent to synchronize a push subscription.  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4  
  
```  
  
 The following example starts the Merge Agent to synchronize a push subscription.  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can synchronize push subscriptions programmatically by using Replication Management Objects \(RMO\) and managed code access to replication agent functionalities. The classes that you use to synchronize a push subscription depend on the type of publication to which the subscription belongs.  
  
> [!NOTE]  
>  If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously. However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process \(for example, if you want to display a progress bar\), you should start the agent synchronously. For [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssExpressEd2005](../../Token\Other/ssExpressEd2005_md.md)] Subscribers, you must start the agent synchronously.  
  
#### To synchronize a push subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) class and set the following properties:  
  
    -   The publication database name for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName).  
  
    -   The name of the publication to which the subscription belongs for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName).  
  
    -   The name of the subscription database for [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName).  
  
    -   The name of the Subscriber for [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName).  
  
    -   The connection created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the remaining subscription properties. If this method returns **false**, verify that the subscription exists.  
  
4.  Start the Distribution Agent at the Distributor in one of the following ways:  
  
    -   Call the [SynchronizeWithJob](assetId:///M:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob) method on the instance of [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) from step 2. This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running. You cannot call this method if the subscription was created with a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault).  
  
    -   Obtain an instance of the [TransSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.TransSynchronizationAgent) class from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent) property, and call the [Synchronize](assetId:///M:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize) method. This method starts the agent synchronously, and control remains with the running agent job. During synchronous execution you can handle the [Status](assetId:///E:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status) event while the agent is running.  
  
#### To synchronize a push subscription to a merge publication  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) class, and set the following properties:  
  
    -   The publication database name for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName).  
  
    -   The name of the publication to which the subscription belongs for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName).  
  
    -   The name of the subscription database for [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName).  
  
    -   The name of the Subscriber for [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName).  
  
    -   The connection created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the remaining subscription properties. If this method returns **false**, verify that the subscription exists.  
  
4.  Start the Merge Agent at the Distributor in one of the following ways:  
  
    -   Call the [SynchronizeWithJob](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob) method on the instance of [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) from step 2. This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running. You cannot call this method if the subscription was created with a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault).  
  
    -   Obtain an instance of the [MergeSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.MergeSynchronizationAgent) class from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent) property, and call the [Synchronize](assetId:///M:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize) method. This method starts the Merge Agent synchronously, and control remains with the running agent job. During synchronous execution, you can handle the [Status](assetId:///E:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status) event while the agent is running.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example synchronizes a push subscription to a transactional publication, where the agent is started asynchronously using the agent job.  
  
 [!CODE [HowTo#rmo_SyncTranPushSub_WithJob](../CodeSnippet/SQL15/replication/howto#rmo_synctranpushsub_withjob)]  
  
 [!CODE [HowTo#rmo_vb_SyncTranPushSub_WithJob](../CodeSnippet/SQL15/replication/howto#rmo_vb_synctranpushsub_withjob)]  
  
 This example synchronizes a push subscription to a transactional publication, where the agent is started synchronously.  
  
 [!CODE [HowTo#rmo_SyncTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_synctranpushsub)]  
  
 [!CODE [HowTo#rmo_vb_SyncTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_synctranpushsub)]  
  
 This example synchronizes a push subscription to a merge publication, where the agent is started asynchronously using the agent job.  
  
 [!CODE [HowTo#rmo_SyncMergePushSub_WithJob](../CodeSnippet/SQL15/replication/howto#rmo_syncmergepushsub_withjob)]  
  
 [!CODE [HowTo#rmo_vb_SyncMergePushSub_WithJob](../CodeSnippet/SQL15/replication/howto#rmo_vb_syncmergepushsub_withjob)]  
  
 This example synchronizes a push subscription to a merge publication, where the agent is started synchronously.  
  
 [!CODE [HowTo#rmo_SyncMergePushSub](../CodeSnippet/SQL15/replication/howto#rmo_syncmergepushsub)]  
  
 [!CODE [HowTo#rmo_vb_SyncMergePushSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_syncmergepushsub)]  
  
## See Also  
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Synchronize Data](../../Topics\TopicNameNotContainA/Synchronize-Data.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  