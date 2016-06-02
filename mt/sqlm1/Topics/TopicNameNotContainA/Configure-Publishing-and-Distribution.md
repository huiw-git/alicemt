---
title: Configure Publishing and Distribution
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cfc8966-833e-42fa-80cb-09175d1feed7
---
# Configure Publishing and Distribution
  This topic describes how to configure publishing and distribution in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To configure publishing and distribution, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For more information, see [Secure Deployment &#40;Replication&#41;](../Topic/Secure%20Deployment%20\(Replication\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Configure distribution using the New Publication Wizard or the Configure Distribution Wizard. After the Distributor is configured, view and modify properties in the **Distributor Properties \- \<Distributor\>** dialog box. Use the Configure Distribution Wizard if you want to configure a Distributor so that members of the **db\_owner** fixed database roles can create publications, or because you want to configure a remote Distributor that is not a Publisher.  
  
#### To configure distribution  
  
1.  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to the server that will be the Distributor \(in many cases, the Publisher and Distributor are the same server\), and then expand the server node.  
  
2.  Right\-click the **Replication** folder, and then click **Configure Distribution**.  
  
3.  Follow the Configure Distribution Wizard to:  
  
    -   Select a Distributor. To use a local Distributor, select **'\<ServerName\>' will act as its own Distributor; SQL Server will create a distribution database and log**. To use a remote Distributor, select **Use the following server as the Distributor**, and then select a server. The server must already be configured as a Distributor, and the Publisher must be enabled to use the Distributor. For more information, see [Enable a Remote Publisher at a Distributor &#40;SQL Server Management Studio&#41;](../Topic/Enable%20a%20Remote%20Publisher%20at%20a%20Distributor%20\(SQL%20Server%20Management%20Studio\).md).  
  
         If you select a remote Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor. This password must match the password specified when the Publisher was enabled at the remote Distributor.  
  
    -   Specify a root snapshot folder \(for a local Distributor\). The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it. Each Publisher that uses this Distributor creates a folder under the root folder, and each publication creates folders under the Publisher folder in which to store snapshot files. For more information on securing the folder appropriately, see [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
    -   Specify the distribution database \(for a local Distributor\). The distribution database stores metadata and history data for all types of replication and transactions for transactional replication.  
  
    -   Optionally enable other Publishers to use the Distributor. If other Publishers are enabled to use the Distributor, you must enter a password on the **Distributor Password** page for connections made from these Publishers to the Distributor.  
  
    -   Optionally script configuration settings. For more information, see [Scripting Replication](../../Topics\TopicNameNotContainA/Scripting-Replication.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Replication publishing and distribution can be configured programmatically using replication stored procedures.  
  
#### To configure publishing using a local distributor  
  
1.  Execute [sp_get_distributor &#40;Transact-SQL&#41;](../Topic/sp_get_distributor%20\(Transact-SQL\).md) to determine if the server is already configured as a Distributor.  
  
    -   If the value of **installed** in the result set is **0**, execute [sp_adddistributor &#40;Transact-SQL&#41;](../Topic/sp_adddistributor%20\(Transact-SQL\).md) at the Distributor on the master database.  
  
    -   If the value of **distribution db installed** in the result set is **0**, execute [sp_adddistributiondb &#40;Transact-SQL&#41;](../Topic/sp_adddistributiondb%20\(Transact-SQL\).md) at the Distributor on the master database. Specify the name of the distribution database for **@database**. Optionally, you can specify the maximum transactional retention period for **@max\_distretention** and the history retention period for **@history\_retention**. If a new database is being created, specify the desired database property parameters.  
  
2.  At the Distributor, which is also the Publisher, execute [sp_adddistpublisher &#40;Transact-SQL&#41;](../Topic/sp_adddistpublisher%20\(Transact-SQL\).md), specifying the UNC share that will be used as default snapshot folder for **@working\_directory**.  
  
3.  At the Publisher, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md). Specify the database being published for **@dbname**, the type of replication for **@optname**, and a value of **true** for **@value**.  
  
#### To configure publishing using a remote distributor  
  
1.  Execute [sp_get_distributor &#40;Transact-SQL&#41;](../Topic/sp_get_distributor%20\(Transact-SQL\).md) to determine if the server is already configured as a Distributor.  
  
    -   If the value of **installed** in the result set is **0**, execute [sp_adddistributor &#40;Transact-SQL&#41;](../Topic/sp_adddistributor%20\(Transact-SQL\).md) at the Distributor on the master database. Specify a strong password for **@password**. This password for the **distributor\_admin** account will be used by the Publisher when connecting to the Distributor.  
  
    -   If the value of **distribution db installed** in the result set is **0**, execute [sp_adddistributiondb &#40;Transact-SQL&#41;](../Topic/sp_adddistributiondb%20\(Transact-SQL\).md) at the Distributor on the master database. Specify the name of the distribution database for **@database**. Optionally, you can specify the maximum transactional retention period for **@max\_distretention** and the history retention period for **@history\_retention**. If a new database is being created, specify the desired database property parameters.  
  
2.  At the Distributor, execute [sp_adddistpublisher &#40;Transact-SQL&#41;](../Topic/sp_adddistpublisher%20\(Transact-SQL\).md), specifying the UNC share that will be used as default snapshot folder for **@working\_directory**. If the Distributor will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@login** and **@password**.  
  
3.  At the Publisher on the master database, execute [sp_adddistributor &#40;Transact-SQL&#41;](../Topic/sp_adddistributor%20\(Transact-SQL\).md). Specify the strong password used in step 1 for **@password**. This password will be used by the Publisher when connecting to the Distributor.  
  
4.  At the Publisher, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md). Specify the database being published for **@dbname**, the type of replication for **@optname**, and a value of true for **@value**.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 The following example demonstrates how to configure publishing and distribution programmatically. In this example, the name of the server that is being configured as a publisher and a local distributor is supplied using scripting variables. Replication publishing and distribution can be configured programmatically using replication stored procedures.  
  
 [!CODE [HowTo#AddDistPub](../CodeSnippet/SQL15/replication/howto#adddistpub)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
  
#### To configure publishing and distribution on a single server  
  
1.  Create a connection to the server by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
3.  Create an instance of the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) class.  
  
4.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionDatabase.Name) property to the database name and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
5.  Install the Distributor by calling the [InstallDistributor](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor(System.String,Microsoft.SqlServer.Replication.DistributionDatabase)) method. Pass the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) object from step 3.  
  
6.  Create an instance of the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) class.  
  
7.  Set the following properties of [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher):  
  
    -   [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.Name) \- name of the Publisher.  
  
    -   [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) \- the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
    -   [DistributionDatabase](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase) \- the name of the database created in step 5.  
  
    -   [WorkingDirectory](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory) \- the share used to access snapshot files.  
  
    -   [PublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity) \- the security mode used when connecting to the Publisher. [WindowsAuthentication](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication) is recommended.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.DistributionPublisher.Create) method.  
  
#### To configure publishing and distribution using a remote Distributor  
  
1.  Create a connection to the remote Distributor server by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
3.  Create an instance of the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) class.  
  
4.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionDatabase.Name) property to the database name, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
5.  Install the Distributor by calling the [InstallDistributor](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor(System.String,Microsoft.SqlServer.Replication.DistributionDatabase)) method. Specify a secure password \(used by the Publisher when connecting to the remote Distributor\) and the [DistributionDatabase](assetId:///T:Microsoft.SqlServer.Replication.DistributionDatabase) object from step 3. For more information, see [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md).  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows .NET Framework.  
  
6.  Create an instance of the [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher) class.  
  
7.  Set the following properties of [DistributionPublisher](assetId:///T:Microsoft.SqlServer.Replication.DistributionPublisher):  
  
    -   [Name](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.Name) \- name of the local Publisher server.  
  
    -   [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) \- the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
    -   [DistributionDatabase](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase) \- the name of the database created in step 5.  
  
    -   [WorkingDirectory](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory) \- the share used to access snapshot files.  
  
    -   [PublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity) \- the security mode used when connecting to the Publisher. [WindowsAuthentication](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication) is recommended.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.DistributionPublisher.Create) method.  
  
9. Create a connection to the local Publisher server by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
10. Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 9.  
  
11. Call the [InstallDistributor](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor(System.String,System.String)) method. Pass the name of the remote Distributor and the password for the remote Distributor specified in step 5.  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the Windows .NET Framework.  
  
###  <a name="PShellExample"></a> Example \(RMO\)  
 You can programmatically configure replication publishing and distribution by using Replication Management Objects \(RMO\).  
  
 [!CODE [HowTo#rmo_AddDistPub](../CodeSnippet/SQL15/replication/howto#rmo_adddistpub)]  
  
 [!CODE [HowTo#rmo_vb_AddDistPub](../CodeSnippet/SQL15/replication/howto#rmo_vb_adddistpub)]  
  
## See Also  
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Configure Replication for AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/Configure%20Replication%20for%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  