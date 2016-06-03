---
title: Delete a Publication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
---
# Delete a Publication
  This topic describes how to delete a publication in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To delete a publication, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Delete publications from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
#### To delete a publication  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Right\-click the publication you want to delete, and then click **Delete**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Publications can be deleted programmatically using replication stored procedures. The stored procedures that you use depend on the type of publication being deleted.  
  
> [!NOTE]  
>  Deleting a publication does not remove published objects from the publication database or the corresponding objects from the subscription database. Use the `DROP <object>` command to manually remove these objects if necessary.  
  
#### To delete a snapshot or transactional publication  
  
1.  Do one of the following:  
  
    -   To delete a single publication, execute [sp\_droppublication](../Topic/sp_droppublication%20\(Transact-SQL\).md) at the Publisher on the publication database.  
  
    -   To delete all publications in and remove all replication objects from a published database, execute [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) at the Publisher. Specify a value of **tran** for **@type**. \(Optional\) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **@force**. \(Optional\) Specify the name of the database for **@dbname** if [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) is not executed on the publication database.  
  
        > [!NOTE]  
        >  Specifying a value of **1** for **@force** may leave replication\-related publishing objects in the database.  
  
2.  \(Optional\) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md) to disable publication of the current database using snapshot or transactional replication.  
  
3.  \(Optional\) At the Subscriber on the subscription database, execute [sp\_subscription\_cleanup](../Topic/sp_subscription_cleanup%20\(Transact-SQL\).md) to remove any remaining replication metadata in the subscription database.  
  
#### To delete a merge publication  
  
1.  Do one of the following:  
  
    -   To delete a single publication, execute [sp_dropmergepublication &#40;Transact-SQL&#41;](../Topic/sp_dropmergepublication%20\(Transact-SQL\).md) at the Publisher on the publication database.  
  
    -   To delete all publications in and remove all replication objects from a published database, execute [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) at the Publisher. Specify a value of **merge** for **@type**. \(Optional\) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **@force**. \(Optional\) Specify the name of the database for **@dbname** if [sp\_removedbreplication](../Topic/sp_removedbreplication%20\(Transact-SQL\).md) is not executed on the publication database.  
  
        > [!NOTE]  
        >  Specifying a value of **1** for **@force** may leave replication\-related publishing objects in the database.  
  
2.  \(Optional\) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md) to disable publication of the current database using merge replication.  
  
3.  \(Optional\) At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../Topic/sp_mergesubscription_cleanup%20\(Transact-SQL\).md) to remove any remaining replication metadata in the subscription database.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example shows how to remove a transactional publication and disable transactional publishing for a database. This example assumes that all subscriptions were previously removed. For more information, see [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md) or [Delete a Push Subscription](../../Topics\TopicNameContainA/Delete-a-Push-Subscription.md).  
  
 [!CODE [HowTo#sp_droppublication](../CodeSnippet/SQL15/replication/howto#sp_droppublication)]  
  
 This example shows how to remove a merge publication and disable merge publishing for a database. This example assumes that all subscriptions were previously removed. For more information, see [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md) or [Delete a Push Subscription](../../Topics\TopicNameContainA/Delete-a-Push-Subscription.md).  
  
 [!CODE [HowTo#sp_dropmergepublication](../CodeSnippet/SQL15/replication/howto#sp_dropmergepublication)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can delete publications programmatically by using Replication Management Objects \(RMO\). The RMO classes that you use to remove a publication depend on the type of publication you remove.  
  
#### To remove a snapshot or transactional publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class.  
  
3.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name) and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the connection created in step 1.  
  
4.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the publication exists. If the value of this property is **false**, either the publication properties in step 3 were defined incorrectly or the publication does not exist.  
  
5.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Publication.Remove) method.  
  
6.  \(Optional\) If no other transactional publications exist for this database, the database can be disabled for transactional publishing as follows:  
  
    1.  Create an instance of the [ReplicationDatabase](assetId:///T:Microsoft.SqlServer.Replication.ReplicationDatabase) class. Set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the instance of [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
    2.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, confirm that the database exists.  
  
    3.  Set the [EnabledTransPublishing](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing) property to **false**.  
  
    4.  Call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  Close the connections.  
  
#### To remove a merge publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class.  
  
3.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name) and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the connection created in step 1.  
  
4.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the publication exists. If the value of this property is **false**, either the publication properties in step 3 were defined incorrectly or the publication does not exist.  
  
5.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Publication.Remove) method.  
  
6.  \(Optional\) If no other merge publications exist for this database, the database can be disabled for merge publishing as follows:  
  
    1.  Create an instance of the [ReplicationDatabase](assetId:///T:Microsoft.SqlServer.Replication.ReplicationDatabase) class. Set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the instance of [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from Step 1.  
  
    2.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, verify that the database exists.  
  
    3.  Set the [EnabledMergePublishing](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing) property to **false**.  
  
    4.  Call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method.  
  
7.  Close the connections.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 The following example deletes a transactional publication. If no other transactional publications exist for this database, transactional publishing is also disabled.  
  
 [!CODE [HowTo#rmo_DropTranPub](../CodeSnippet/SQL15/replication/howto#rmo_droptranpub)]  
  
 [!CODE [HowTo#rmo_vb_DropTranPub](../CodeSnippet/SQL15/replication/howto#rmo_vb_droptranpub)]  
  
 The following example deletes a merge publication. If no other merge publications exist for this database, merge publishing is also disabled.  
  
 [!CODE [HowTo#rmo_DropMergePub](../CodeSnippet/SQL15/replication/howto#rmo_dropmergepub)]  
  
 [!CODE [HowTo#rmo_vb_DropMergePub](../CodeSnippet/SQL15/replication/howto#rmo_vb_dropmergepub)]  
  
## See Also  
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)  
  
  