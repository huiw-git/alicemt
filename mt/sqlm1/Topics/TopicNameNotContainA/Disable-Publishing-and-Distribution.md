---
title: Disable Publishing and Distribution
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
---
# Disable Publishing and Distribution
  This topic describes how to disable publishing and distribution in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 You can do the following:  
  
-   Delete all distribution databases on the Distributor.  
  
-   Disable all Publishers that use the Distributor and delete all publications on those Publishers.  
  
-   Delete all subscriptions to the publications. Data in the publication and subscription databases will not be deleted; however, it loses its synchronization relationship to any publication databases. If you want the data at the Subscriber to be deleted, you must delete it manually.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
-   **To disable publishing and distribution, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   To disable publishing and distribution, all distribution and publication databases must be online. If any *database snapshots* exist for distribution or publication databases, they must be dropped before disabling publishing and distribution. A database snapshot is a read\-only offline copy of a database and is not related to a replication snapshot. For more information, see [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Disable publishing and distribution by using the Disable Publishing and Distribution Wizard.  
  
#### To disable publishing and distribution  
  
1.  Connect to the Publisher or Distributor you want to disable in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Right\-click the **Replication** folder, and then click **Disable Publishing and Distribution**.  
  
3.  Complete the steps in the Disable Publishing and Distribution Wizard.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Publishing and distributing can be disabled programmatically using replication stored procedures.  
  
#### To disable publishing and distribution  
  
1.  Stop all replication\-related jobs. For a list of job names, see the "Agent Security Under SQL Server Agent" section of [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
2.  At each Subscriber on the subscription database, execute [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) to remove replication objects from the database. This stored procedure will not remove replication jobs at the Distributor.  
  
3.  At the Publisher on the publication database, execute [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) to remove replication objects from the database.  
  
4.  If the Publisher uses a remote Distributor, execute [sp\_dropdistributor](../Topic/sp_dropdistributor%20\(Transact-SQL\).md).  
  
5.  At the Distributor, execute [sp\_dropdistpublisher](../Topic/sp_dropdistpublisher%20\(Transact-SQL\).md). This stored procedure should be run once for each Publisher registered at the Distributor.  
  
6.  At the Distributor, execute [sp\_dropdistributiondb](../Topic/sp_dropdistributiondb%20\(Transact-SQL\).md) to delete the distribution database. This stored procedure should be run once for each distribution database at the Distributor. This also removes any Queue Reader Agent jobs associated with the distribution database.  
  
7.  At the Distributor, execute [sp\_dropdistributor](../Topic/sp_dropdistributor%20\(Transact-SQL\).md) to remove the Distributor designation from the server.  
  
    > [!NOTE]  
    >  If all replication publishing and distribution objects are not dropped before you execute [sp\_dropdistpublisher](../Topic/sp_dropdistpublisher%20\(Transact-SQL\).md) and [sp\_dropdistributor](../Topic/sp_dropdistributor%20\(Transact-SQL\).md), these procedures will return an error. To drop all replication\-related objects when a Publisher or Distributor is dropped, the **@no\_checks** parameter must be set to **1**. If a Publisher or Distributor is offline or unreachable, the **@ignore\_distributor** parameter can be set to **1** so that they can be dropped; however, any publishing and distributing objects left behind must be removed manually.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example script removes replication objects from the subscription database.  
  
 [!CODE [HowTo#sp_removedbreplication](../CodeSnippet/SQL15/replication/howto#sp_removedbreplication)]  
  
 This example script disables publishing and distribution on a server that is a Publisher and Distributor and drops the distribution database.  
  
 [!CODE [HowTo#sp_DropDistPub](../CodeSnippet/SQL15/replication/howto#sp_dropdistpub)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
  
#### To disable publishing and distribution  
  
1.  Remove all subscriptions to publications that use the Distributor. For more information, see [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md) and [Delete a Push Subscription](../../Topics\TopicNameContainA/Delete-a-Push-Subscription.md).  
  
2.  Remove all publications that use the Distributor, and disable publishing for all databases if the Publisher and Distributor are on the same server. For more information, see [Delete a Publication](../../Topics\TopicNameContainA/Delete-a-Publication.md).  
  
3.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
4.  Create an instance of the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) class. Specify the [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.Name) property, and pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 3.  
  
5.  \(Optional\) Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object and verify that the Publisher exists. If this method returns **false**, the Publisher name set in step 4 was incorrect or the Publisher is not used by this Distributor.  
  
6.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.DistributionPublisher.Remove(System.Boolean)) method. Pass a value of **true** for *force* if the Publisher and Distributor are on different servers, and when the Publisher should be uninstalled at the Distributor without first verifying that publications no longer exist at the Publisher.  
  
7.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 3.  
  
8.  Call the [UninstallDistributor](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor(System.Boolean)) method. Pass a value of **true** for *force* to remove all replication objects at the Distributor without first verifying that all local publication databases have been disabled, and distribution databases have been uninstalled.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example removes the Publisher registration at the Distributor, drops the distribution database, and uninstalls the Distributor.  
  
 [!CODE [HowTo#rmo_DropDistPub](../CodeSnippet/SQL15/replication/howto#rmo_dropdistpub)]  
  
 [!CODE [HowTo#rmo_vb_DropDistPub](../CodeSnippet/SQL15/replication/howto#rmo_vb_dropdistpub)]  
  
 This example uninstalls the Distributor without first disabling local publication databases or dropping the distribution database.  
  
 [!CODE [HowTo#rmo_DropDistPubForce](../CodeSnippet/SQL15/replication/howto#rmo_dropdistpubforce)]  
  
 [!CODE [HowTo#rmo_vb_DropDistPubForce](../CodeSnippet/SQL15/replication/howto#rmo_vb_dropdistpubforce)]  
  
## See Also  
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)  
  
  