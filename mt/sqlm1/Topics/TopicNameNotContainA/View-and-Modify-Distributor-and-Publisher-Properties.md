---
title: View and Modify Distributor and Publisher Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
---
# View and Modify Distributor and Publisher Properties
  This topic describes how to view and modify Distributor and Publisher properties in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To view and modify Distributor and Publisher properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   For Publishers running versions prior to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], a user in the **sysadmin** fixed server role can register Subscribers on the **Subscribers** page. Beginning with [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], it is no longer necessary to explicitly register Subscribers for replication.  
  
###  <a name="Security"></a> Security  
 When possible, prompt users to enter security credentials at runtime.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view and modify Distributor properties  
  
1.  Connect to the Distributor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Right\-click the **Replication** folder, and then click **Distributor Properties**.  
  
3.  View and modify properties in the **Distributor Properties \- \<Distributor\>** dialog box.  
  
    -   To view and modify properties for a distribution database, click the properties button \(**...**\) for the database on the **General** page of thedialog box.  
  
    -   To view and modify Publisher properties associated with the Distributor, click the properties button \(**...**\) for the Publisher on the **Publishers** page of the dialog box.  
  
    -   To access profiles for replication agents, click the **Profile Defaults** button on the **General** page of the dialog box. For more information, see [Replication Agent Profiles](../../Topics\TopicNameNotContainA/Replication-Agent-Profiles.md).  
  
    -   To change the password for the account used when administrative stored procedures execute at the Publisher and update information at the Distributor, enter a new password in the **Password** and **Confirm password** boxes on the **Publishers** page of the dialog box. For more information, see [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md).  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
#### To view and modify Publisher properties  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Right\-click the **Replication** folder, and then click **Publisher Properties**.  
  
3.  View and modify properties in the **Publisher Properties \- \< Publisher \>** dialog box.  
  
    -   A user in the **sysadmin** fixed server role can enable databases for replication on the **Publication Databases** page. Enabling a database does not publish that database; rather, it allows any user in the **db\_owner** fixed database role for that database to create one or more publications in the database.  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Publisher and Distributor properties can be viewed programmatically using replication stored procedures.  
  
#### To view Distributor and distribution database properties  
  
1.  Execute [sp\_helpdistributor](../Topic/sp_helpdistributor%20\(Transact-SQL\).md) to return information about the Distributor, distribution database, and working directory.  
  
2.  Execute [sp\_helpdistributiondb](../Topic/sp_helpdistributiondb%20\(Transact-SQL\).md) to return properties of a specified distribution database.  
  
#### To change Distributor and distribution database properties  
  
1.  At the Distributor, execute [sp\_changedistributor\_property](../Topic/sp_changedistributor_property%20\(Transact-SQL\).md) to modify Distributor properties.  
  
2.  At the Distributor, execute [sp\_changedistributiondb](../Topic/sp_changedistributiondb%20\(Transact-SQL\).md) to modify distribution database properties.  
  
3.  At the Distributor, execute [sp\_changedistributor\_password](../Topic/sp_changedistributor_password%20\(Transact-SQL\).md) to change the Distributor password.  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, secure the file to prevent unauthorized access.  
  
4.  At the Distributor, execute [sp\_changedistpublisher](../Topic/sp_changedistpublisher%20\(Transact-SQL\).md) to change the properties of a Publisher using the Distributor.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 The following example [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script returns information about the Distributor and distribution database.  
  
 [!CODE [HowTo#sp_helpdistributor](../CodeSnippet/SQL15/replication/howto#sp_helpdistributor)]  
  
 [!CODE [HowTo#sp_helpdistributiondb](../CodeSnippet/SQL15/replication/howto#sp_helpdistributiondb)]  
  
 This example changes retention periods for the Distributor, the password used when connecting to the Distributor, and the interval at which the Distributor checks the status of various replication agents \(also known as the heartbeat interval\).  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, secure the file to prevent unauthorized access.  
  
 [!CODE [HowTo#sp_changedistributor_property](../CodeSnippet/SQL15/replication/howto#sp_changedistributor_property)]  
  
 [!CODE [HowTo#sp_changedistributiondb](../CodeSnippet/SQL15/replication/howto#sp_changedistributiondb)]  
  
 [!CODE [HowTo#sp_changedistributor_password](../CodeSnippet/SQL15/replication/howto#sp_changedistributor_password)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
  
#### To view and modify Distributor properties  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 1.  
  
3.  \(Optional\) Check the [IsDistributor](assetId:///P:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor) property to verify that the currently connected server is a Distributor.  
  
4.  Call the [Load](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Load) method to get the properties from the server.  
  
5.  \(Optional\) To change properties, set a new value for one or more of the Distributor properties that can be set on the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) object.  
  
6.  \(Optional\) If the [CachePropertyChanges](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges) property on the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) object is set to **true**, call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method to commit the changes to the server.  
  
#### To view and modify distribution database properties  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) class. Specify the name property and pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 1.  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties from the server. If this method returns **false**, the database with the specified name does not exist on the server.  
  
4.  \(Optional\) To change properties, set a new value for one of the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) properties that can be set.  
  
5.  \(Optional\) If the [CachePropertyChanges](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges) property on the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) object is set to **true**, call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method to commit the changes to the server.  
  
#### To view and modify Publisher properties  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) class. Specify the [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.Name) property and pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 1.  
  
3.  \(Optional\) To change properties, set a new value for one of the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) properties that can be set.  
  
4.  \(Optional\) If the [CachePropertyChanges](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges) property on the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) object is set to **true**, call the [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) method to commit the changes to the server.  
  
#### To change the password for the administrative connection from the Publisher to the Distributor  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class.  
  
3.  Set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the connection created in step 1.  
  
4.  Call the [Load](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Load) method to get the properties of the object.  
  
5.  Call the [ChangeDistributorPassword](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword(System.String)) method. Pass the new password value for the *password* parameter.  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows .NET Framework.  
  
6.  \(Optional\) Perform the following steps to change the password at each remote Publisher that uses this Distributor:  
  
    1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
    2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class.  
  
    3.  Set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the connection created in step 6a.  
  
    4.  Call the [Load](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.Load) method to get the properties of the object.  
  
    5.  Call the [ChangeDistributorPassword](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword(System.String)) method. Pass the new password value from Step 5 for the *password* parameter.  
  
###  <a name="PShellExample"></a> Example \(RMO\)  
 This example shows how to change Distribution and distribution database properties.  
  
> [!IMPORTANT]  
>  To avoid storing credentials in the code, the new Distributor password is supplied at runtime.  
  
 [!CODE [HowTo#rmo_ChangeDistPub](../CodeSnippet/SQL15/replication/howto#rmo_changedistpub)]  
  
 [!CODE [HowTo#rmo_vb_ChangeDistPub](../CodeSnippet/SQL15/replication/howto#rmo_vb_changedistpub)]  
  
## See Also  
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Disable Publishing and Distribution](../../Topics\TopicNameNotContainA/Disable-Publishing-and-Distribution.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Distributor and Publisher Information Script](../../Topics\TopicNameNotContainA/Distributor-and-Publisher-Information-Script.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [View Information and Perform Tasks for a Publisher &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Publisher%20\(Replication%20Monitor\).md)  
  
  