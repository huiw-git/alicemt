---
title: Programmatically Monitor Replication
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
---
# Programmatically Monitor Replication
  Replication Monitor is a graphical tool that allows you to monitor a replication topology. You can access the same monitoring data programmatically by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] replication stored procedures or replication management objects \(RMO\). These objects enable you to program the following tasks:  
  
-   Monitor the state of Publishers, publications, and subscriptions.  
  
-   Monitor Merge Agent sessions at one or more Subscribers.  
  
-   Monitor transactional commands waiting to be applied at one or more Subscribers.  
  
-   Define the threshold metrics that determine when a publication requires intervention.  
  
-   Monitor the status of tracer tokens.  
  
 **In this topic:**  
  
 [Transact\-SQL](#Tsql)  
  
 [Replication Management Objects \(RMO\)](#RMO)  
  
##  <a name="Tsql"></a> Transact\-SQL  
  
#### To monitor Publishers, publications, and subscriptions from the Distributor  
  
1.  At the Distributor on the distribution database, execute [sp\_replmonitorhelppublisher](../Topic/sp_replmonitorhelppublisher%20\(Transact-SQL\).md). This returns monitoring information for all Publishers using this Distributor. To limit the result set to a single Publisher, specify **@publisher**.  
  
2.  At the Distributor on the distribution database, execute [sp\_replmonitorhelppublication](../Topic/sp_replmonitorhelppublication%20\(Transact-SQL\).md). This returns monitoring information for all publications using this Distributor. To limit the result set to a single Publisher, publication, or published database, specify **@publisher**, **@publication**, or **@publisher\_db**, respectively.  
  
3.  At the Distributor on the distribution database, execute [sp\_replmonitorhelpsubscription](../Topic/sp_replmonitorhelpsubscription%20\(Transact-SQL\).md). This returns monitoring information for all subscriptions using this Distributor. To limit the result set to subscriptions belonging to a single Publisher, publication, or published database, specify **@publisher**, **@publication**, or **@publisher\_db**, respectively.  
  
#### To monitor transactional commands waiting to be applied at the Subscriber  
  
1.  At the Distributor on the distribution database, execute [sp\_replmonitorsubscriptionpendingcmds](../Topic/sp_replmonitorsubscriptionpendingcmds%20\(Transact-SQL\).md). This returns monitoring information for all commands pending for all subscriptions using this Distributor. To limit the result set to commands pending for subscriptions belonging to a single Publisher, Subscriber, publication, or published database, specify **@publisher**, **@subscriber**, **@publication**, or **@publisher\_db**, respectively.  
  
#### To monitor merge changes waiting to be uploaded or downloaded  
  
1.  At the Publisher on the publication database, execute [sp\_showpendingchanges](../Topic/sp_showpendingchanges%20\(Transact-SQL\).md). This returns a result set showing information on changes that are waiting to be replicated to Subscribers. To limit the result set to changes that belong to a single publication or article, specify **@publication** or **@article**, respectively.  
  
2.  At a Subscriber on the subscription database, execute [sp\_showpendingchanges](../Topic/sp_showpendingchanges%20\(Transact-SQL\).md). This returns a result set showing information on changes that are waiting to be replicated to the Publisher. To limit the result set to changes that belong to a single publication or article, specify **@publication** or **@article**, respectively.  
  
#### To monitor Merge Agent sessions  
  
1.  At the Distributor on the distribution database, execute [sp\_replmonitorhelpmergesession](../Topic/sp_replmonitorhelpmergesession%20\(Transact-SQL\).md). This returns monitoring information, including **Session\_id**, on all Merge Agent sessions for all subscriptions using this Distributor. You can also obtain **Session\_id** by querying the [MSmerge\_sessions](../Topic/MSmerge_sessions%20\(Transact-SQL\).md) system table.  
  
2.  At the Distributor on the distribution database, execute [sp\_replmonitorhelpmergesessiondetail](../Topic/sp_replmonitorhelpmergesessiondetail%20\(Transact-SQL\).md). Specify a **Session\_id** value from step 1 for **@session\_id**. This displays detailed monitor information about the session.  
  
3.  Repeat step 2 for each session of interest.  
  
#### To monitor Merge Agent sessions for pull subscriptions from the Subscriber  
  
1.  At the Subscriber on the subscription database, execute [sp\_replmonitorhelpmergesession](../Topic/sp_replmonitorhelpmergesession%20\(Transact-SQL\).md). For a given subscription, specify **@publisher**, **@publication**, and the name of the publication database for **@publisher\_db**. This returns monitoring information for the last five Merge Agent sessions for this subscription. Note the value of **Session\_id** for sessions of interest in the result set.  
  
2.  At the Subscriber on the subscription database, execute [sp\_replmonitorhelpmergesessiondetail](../Topic/sp_replmonitorhelpmergesessiondetail%20\(Transact-SQL\).md). Specify a **Session\_id** value from step 1 for **@session\_id**. This displays detailed monitoring information about the session.  
  
3.  Repeat step 2 for each session of interest.  
  
#### To view and modify the monitor threshold metrics for a publication  
  
1.  At the Distributor on the distribution database, execute [sp\_replmonitorhelppublicationthresholds](../Topic/sp_replmonitorhelppublicationthresholds%20\(Transact-SQL\).md). This returns the monitoring thresholds set for all publications using this Distributor. To limit the result set to monitor thresholds to publications belonging to a single Publisher or published database or to a single publication, specify **@publisher**, **@publisher\_db**, or **@publication**, respectively. Note the value of **Metric\_id** for any thresholds that must be changed. For more information, see [Set Thresholds and Warnings in Replication Monitor](../../Topics\TopicNameNotContainA/Set-Thresholds-and-Warnings-in-Replication-Monitor.md).  
  
2.  At the Distributor on the distribution database, execute [sp\_replmonitorchangepublicationthreshold](../Topic/sp_replmonitorchangepublicationthreshold%20\(Transact-SQL\).md). Specify the following as needed:  
  
    -   The **Metric\_id** value obtained in step 1 for **@metric\_id**.  
  
    -   A new value for the monitor threshold metric for **@value**.  
  
    -   A value of **1** for **@shouldalert** for an alert to be logged when this threshold is reached, or a value of **0** if an alert is not needed.  
  
    -   A value of **1** for **@mode** to enable the monitor threshold metric or a value of **2** to disable it.  
  
##  <a name="RMO"></a> Replication Management Objects \(RMO\)  
  
#### To monitor a subscription to a merge publication at the Subscriber  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeSubscriberMonitor](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscriberMonitor) class, and set the [Publisher](assetId:///P:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher), [Publication](assetId:///P:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication), [PublisherDB](assetId:///P:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB), [SubscriberDB](assetId:///P:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB) properties for the subscription, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1.  
  
3.  Call one of the following methods to return information on Merge Agent sessions for this subscription:  
  
    -   [GetSessionsSummary&#40;&#41;](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary) \- returns an array of [MergeSessionSummary](assetId:///T:Microsoft.SqlServer.Replication.MergeSessionSummary) objects with information on up to the last five Merge Agent sessions. Note the [SessionId](assetId:///P:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId) value for any sessions of interest.  
  
    -   [GetSessionsSummary&#40;Int32&#41;](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary(System.Int32)) \- returns an array of [MergeSessionSummary](assetId:///T:Microsoft.SqlServer.Replication.MergeSessionSummary) objects with information on Merge Agent sessions that have occurred during the past number of hours passed in as the *hours* parameter \(up to the last five sessions\). Note the [SessionId](assetId:///P:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId) value for any sessions of interest.  
  
    -   [GetLastSessionSummary](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary) \- returns a [MergeSessionSummary](assetId:///T:Microsoft.SqlServer.Replication.MergeSessionSummary) object with information on the last Merge Agent session. Note the [SessionId](assetId:///P:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId) value for this session.  
  
    -   [GetSessionsSummaryDataSet](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object with information on up to the last five Merge Agent sessions, one in each row. Note the value of the **Session\_id** column for any sessions of interest.  
  
    -   [GetLastSessionSummaryDataRow](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow) \- returns a [DataRow](assetId:///T:System.Data.DataRow) object with information on the last Merge Agent session. Note the value of the **Session\_id** column for this session.  
  
4.  \(Optional\) Call [RefreshSessionSummary&#40;MergeSessionSummary&#41;](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary(Microsoft.SqlServer.Replication.MergeSessionSummary@)) to refresh the data for the [MergeSessionSummary](assetId:///T:Microsoft.SqlServer.Replication.MergeSessionSummary) object passed as *mss,* or call [RefreshSessionSummary&#40;DataRow&#41;](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary(System.Data.DataRow@)) to refresh the data in the [DataRow](assetId:///T:System.Data.DataRow) object passed as *drRefresh*.  
  
5.  Using the session ID obtained in step 3, call one of the following methods to return information on the details of a particular session:  
  
    -   [GetSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails(System.Int32)) \- returns an array of [MergeSessionDetail](assetId:///T:Microsoft.SqlServer.Replication.MergeSessionDetail) objects for the supplied *SessionId*.  
  
    -   [GetSessionDetailsDataSet](assetId:///M:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet(System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object with information for the specified *SessionId*.  
  
#### To monitor replication properties for all publications at a Distributor  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.ReplicationMonitor) class.  
  
3.  Set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1.  
  
4.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object.  
  
5.  Execute one or more of the following methods to return replication information for all Publishers that use this Distributor.  
  
    -   [EnumDistributionAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Distribution Agents at this Distributor.  
  
    -   [EnumErrorRecords](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords(System.String,System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about errors stored at the Distributor.  
  
    -   [EnumLogReaderAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Log Reader Agents at the Distributor.  
  
    -   [EnumMergeAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Merge Agents at the Distributor.  
  
    -   [EnumMiscellaneousAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all other replication agents at the Distributor.  
  
    -   [EnumPublishers](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Publishers at this Distributor.  
  
    -   [EnumPublishers2](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that returns the Publishers that use this Distributor.  
  
    -   [EnumQueueReaderAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Queue Reader Agents at the Distributor.  
  
    -   [EnumQueueReaderAgentSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails(System.String,System.Int32,System.String)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains details about the specified Queue Reader Agent and session.  
  
    -   [EnumQueueReaderAgentSessions](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions(System.String,System.Int32,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains session information about the specified Queue Reader Agent.  
  
    -   [EnumSnapshotAgents](assetId:///M:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all Snapshot Agents at the Distributor.  
  
#### To monitor publication properties for a specific Publisher at the Distributor  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Get a [PublisherMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitor) object in one of these ways.  
  
    -   Create an instance of the [PublisherMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitor) class. Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.PublisherMonitor.Name) property for the Publisher, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1. Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the Publisher name was defined incorrectly or the publication does not exist.  
  
    -   From the [PublisherMonitorCollection](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitorCollection) accessed by means of the [PublisherMonitors](assetId:///P:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors) property of an existing [ReplicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.ReplicationMonitor) object.  
  
3.  Execute one or more of the following methods to return replication information for all publications that belong to this Publisher.  
  
    -   [EnumDistributionAgentSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails(System.String,System.String)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains details about the specified Distribution Agent and session.  
  
    -   [EnumDistributionAgentSessions](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions(System.String,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains session information about the specified Distribution Agent.  
  
    -   [EnumErrorRecords](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords(System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains error record information about the specified error.  
  
    -   [EnumLogReaderAgentSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails(System.String,System.String)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains details for the specified Log Reader Agent and session.  
  
    -   [EnumLogReaderAgentSessions](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions(System.String,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains session information for the specified Log Reader Agent.  
  
    -   [EnumMergeAgentSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails(System.String,System.String)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains details about the specified Merge Agent and session.  
  
    -   [EnumMergeAgentSessionDetails2](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2(System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains additional details about the specified Merge Agent and session.  
  
    -   [EnumMergeAgentSessions](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions(System.String,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains session information for the specified Merge Agent.  
  
    -   [EnumMergeAgentSessions2](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2(System.String,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains additional session information for the specified Merge Agent.  
  
    -   [EnumPublications](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all publications at this Distributor.  
  
    -   [EnumPublications2](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains additional information about all publications at this Distributor.  
  
    -   [EnumSnapshotAgentSessionDetails](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails(System.String,System.String)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains details about the specified Snapshot Agent and session.  
  
    -   [EnumSnapshotAgentSessions](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions(System.String,System.Int32,System.Boolean)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains session information for the specified Snapshot Agent.  
  
    -   [EnumSubscriptions](assetId:///M:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions(Microsoft.SqlServer.Replication.PublicationType,Microsoft.SqlServer.Replication.SubscriptionResultOption)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all subscriptions to publications at this Distributor.  
  
#### To monitor properties for a specific publication at the Distributor  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Get a [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) object in one of these ways.  
  
    -   Create an instance of the [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) class. Set the [DistributionDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName), [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName), and [Name](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.Name) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1. Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the publication properties were defined incorrectly or the publication does not exist.  
  
    -   From the [PublicationMonitorCollection](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitorCollection) accessed by means of the [PublicationMonitors](assetId:///P:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors) property of an existing [PublisherMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitor) object.  
  
3.  Execute one or more of the following methods to return information about this publication.  
  
    -   [EnumErrorRecords](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords(System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains error records about the specified error.  
  
    -   [EnumLogReaderAgent](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about the Log Reader Agent for this publication.  
  
    -   [EnumMonitorThresholds](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about the monitor warning thresholds set for this publication.  
  
    -   [EnumQueueReaderAgent](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about the Queue Reader Agent used by this publication.  
  
    -   [EnumSnapshotAgent](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about the Snapshot Agent for this publication.  
  
    -   [EnumSubscriptions](assetId:///M:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about subscriptions to this publication.  
  
    -   [EnumSubscriptions2](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2(Microsoft.SqlServer.Replication.SubscriptionResultOption)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains additional information about subscriptions to this publication based on the supplied [SubscriptionResultOption](assetId:///T:Microsoft.SqlServer.Replication.SubscriptionResultOption).  
  
    -   [EnumTracerTokenHistory](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory(System.Int32)) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains latency information for the specified tracer token.  
  
    -   [EnumTracerTokens](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens) \- returns a [DataSet](assetId:///T:System.Data.DataSet) object that contains information about all tracer tokens inserted into this publication.  
  
#### To monitor transactional commands that are waiting to be applied at the Subscriber  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Get a [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) object in one of these ways.  
  
    -   Create an instance of the [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) class. Set the [DistributionDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName), [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName), and [Name](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.Name) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1. Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the publication properties were defined incorrectly or the publication does not exist.  
  
    -   From the [PublicationMonitorCollection](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitorCollection) accessed by means of the [PublicationMonitors](assetId:///P:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors) property of an existing [PublisherMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitor) object.  
  
3.  Execute the [TransPendingCommandInfo](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo(System.String,System.String,Microsoft.SqlServer.Replication.SubscriptionOption)) method, which returns a [PendingCommandInfo](assetId:///T:Microsoft.SqlServer.Replication.PendingCommandInfo) object.  
  
4.  Use the properties of this [PendingCommandInfo](assetId:///T:Microsoft.SqlServer.Replication.PendingCommandInfo) object to determine the estimated number of pending commands and the length of time it will take to complete the delivery of these commands.  
  
#### To set the monitor warning thresholds for a publication  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Get a [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) object in one of these ways.  
  
    -   Create an instance of the [PublicationMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitor) class. Set the [DistributionDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName), [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName), [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName), and [Name](assetId:///P:Microsoft.SqlServer.Replication.PublicationMonitor.Name) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) created in step 1. Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the publication properties were defined incorrectly or the publication does not exist.  
  
    -   From the [PublicationMonitorCollection](assetId:///T:Microsoft.SqlServer.Replication.PublicationMonitorCollection) accessed by means of the [PublicationMonitors](assetId:///P:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors) property of an existing [PublisherMonitor](assetId:///T:Microsoft.SqlServer.Replication.PublisherMonitor) object.  
  
3.  Execute the [EnumMonitorThresholds](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds) method. Note the current threshold settings in the returned [ArrayList](assetId:///T:System.Collections.ArrayList) of [MonitorThreshold](assetId:///T:Microsoft.SqlServer.Replication.MonitorThreshold) objects.  
  
4.  Execute the [ChangeMonitorThreshold](assetId:///M:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold(System.Int32,System.Boolean,System.Int32,System.Int32)) method. Pass the following parameters:  
  
    -   *metricID* \- an [Int32](assetId:///T:System.Int32) value that represents the monitoring threshold metric from the following table:  
  
        |Value|Description|  
        |-----------|-----------------|  
        |1|**expiration** \- monitors for imminent expiration of subscriptions to transactional publications.|  
        |2|**latency** \- monitors for the performance of subscriptions to transactional publications.|  
        |4|**mergeexpiration** \- monitors for imminent expiration of subscriptions to merge publications.|  
        |5|**mergeslowrunduration** \- monitors the duration of merge synchronizations over low\-bandwidth \(dialup\) connections.|  
        |6|**mergefastrunduration** \- monitors the duration of merge synchronizations over high\-bandwidth \(LAN\) connections.|  
        |7|**mergefastrunspeed** \- monitors the synchronization rate of merge synchronizations over high\-bandwidth \(LAN\) connections.|  
        |8|**mergeslowrunspeed** \- monitors the synchronization rate of merge synchronizations over low\-bandwidth \(dialup\) connections.|  
  
    -   *enable* \- [Boolean](assetId:///T:System.Boolean) value that indicates whether the metric is enabled for the publication.  
  
    -   *thresholdValue* \- integer value that sets the threshold.  
  
    -   *shouldAlert* \- integer that indicates whether this threshold should generate an alert.  
  
  