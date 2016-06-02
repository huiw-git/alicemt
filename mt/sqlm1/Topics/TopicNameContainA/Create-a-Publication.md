---
title: Create a Publication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
---
# Create a Publication
  This topic describes how to create a publication in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To create a publication and define articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Publication and article names cannot include any of the following characters: % , \* , \[ , \] , | , : , " , ? , ' , \\ , \/ , \< , \>. If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name in the **Article Properties \- \<Article\>** dialog box, which is available from the **Articles** page in the wizard.  
  
###  <a name="Security"></a> Security  
 When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Create publications and define articles with the New Publication Wizard. After a publication is created, view and modify publication properties in the **Publication Properties \- \<Publication\>** dialog box. For information about creating a publication from an Oracle database, see [Create a Publication from an Oracle Database](../../Topics\TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md).  
  
#### To create a publication and define articles  
  
1.  Connect to the Publisher in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then right\-click the **Local Publications** folder.  
  
3.  Click **New Publication**.  
  
4.  Follow the pages in the New Publication Wizard to:  
  
    -   Specify a Distributor if distribution has not been configured on the server. For more information about configuring distribution, see [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md).  
  
         If you specify on the **Distributor** page that the Publisher server will act as its own Distributor \(a local Distributor\), and the server is not configured as a Distributor, the New Publication Wizard will configure the server. You will specify a default snapshot folder for the Distributor on the **Snapshot Folder** page. The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it. For more information about securing the folder appropriately, see [Secure the Snapshot Folder](../../Topics\TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
         If you specify that another server should act as the Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor. This password must match the password specified when the Publisher was enabled at the remote Distributor.  
  
         For more information, see [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md).  
  
    -   Choose a publication database.  
  
    -   Select a publication type. For more information, see [Types of Replication](../../Topics\TopicNameNotContainA/Types-of-Replication.md).  
  
    -   Specify data and database objects to publish; optionally filter columns from table articles, and set article properties.  
  
    -   Optionally filter rows from table articles. For more information, see [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md).  
  
    -   Set the Snapshot Agent schedule.  
  
    -   Specify the credentials under which the following replication agents run and make connections:  
  
         \- Snapshot Agent for all publications.  
  
         \- Log Reader Agent for all transactional publications.  
  
         \- Queue Reader Agent for transactional publications that allow updating subscriptions.  
  
         For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
    -   Optionally script the publication. For more information, see [Scripting Replication](../../Topics\TopicNameNotContainA/Scripting-Replication.md).  
  
    -   Specify a name for the publication.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Publications can be created programmatically using replication stored procedures. The stored procedures that are used will depend on the type of publication being created.  
  
#### To create a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md) to enable publication of the current database using snapshot or transactional replication.  
  
2.  For a transactional publication, determine whether a Log Reader Agent job exists for the publication database. \(This step is not required for snapshot publications.\)  
  
    -   If a Log Reader Agent job exists for the publication database, proceed to step 3.  
  
    -   If you are unsure whether a Log Reader Agent job exists for a published database, execute [sp_helplogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_helplogreader_agent%20\(Transact-SQL\).md) at the Publisher on the publication database.  
  
    -   If the result set is empty, create a Log Reader Agent job. At the Publisher, execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md). Specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows credentials under which the agent runs for **@job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. Proceed to step 3.  
  
3.  At the Publisher, execute [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md). Specify a publication name for **@publication**, and, for the **@repl\_freq** parameter, specify a value of **snapshot** for a snapshot publication or a value of **continuous** for a transactional publication. Specify any other publication options. This defines the publication.  
  
    > [!NOTE]  
    >  Publication names cannot include the following characters:  
    >   
    >  % \* \[ \] | : " ? \\ \/ \< \>  
  
4.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 3 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@snapshot\_job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
5.  Add articles to the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
6.  Start the Snapshot Agent job to generate the initial snapshot for this publication. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
#### To create a merge publication  
  
1.  At the Publisher, execute [sp_replicationdboption &#40;Transact-SQL&#41;](../Topic/sp_replicationdboption%20\(Transact-SQL\).md) to enable publication of the current database using merge replication.  
  
2.  At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md). Specify a name for the publication for **@publication** and any other publication options. This defines the publication.  
  
    > [!NOTE]  
    >  Publication names cannot include the following characters:  
    >   
    >  % \* \[ \] | : " ? \\ \/ \< \>  
  
3.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 2 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@snapshot\_job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
4.  Add articles to the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
5.  Start the Snapshot Agent job to generate the initial snapshot for this publication. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 This example creates a transactional publication. Scripting variables are used to pass Windows credentials that are needed to create jobs for the Snapshot Agent and Log Reader Agent.  
  
 [!CODE [HowTo#sp_AddTranPub](../CodeSnippet/SQL15/replication/howto#sp_addtranpub)]  
  
 This example creates a merge publication. Scripting variables are used to pass Windows credentials that are needed to create the job for the Snapshot Agent.  
  
 [!CODE [HowTo#sp_AddMergePub](../CodeSnippet/SQL15/replication/howto#sp_addmergepub)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can create publications programmatically by using Replication Management Objects \(RMO\). The RMO classes that you use to create a publication depend on the type of publication you create.  
  
#### To create a snapshot or transactional publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationDatabase](assetId:///T:Microsoft.SqlServer.Replication.ReplicationDatabase) class for the publication database, set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the instance of [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1, and call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) returns **false**, verify that the database exists.  
  
3.  If the [EnabledTransPublishing](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing) property is **false**, set it to **true**.  
  
4.  For a transactional publication, check the value of the [LogReaderAgentExists](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists) property. If this property is **true**, a Log Read Agent job already exists for this database. If this property is **false**, do the following:  
  
    -   Set the [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) or [SecurePassword](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword) fields of [LogReaderAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Log Reader Agent runs.  
  
        > [!NOTE]  
        >  Setting [LogReaderAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity) is not required when the publication is created by a member of the **sysadmin** fixed server role. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [LogReaderAgentPublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity) when using SQL Server Authentication to connect to the Publisher.  
  
    -   Call the [CreateLogReaderAgent](assetId:///M:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent) method to create the Log Reader Agent job for the database.  
  
5.  Create an instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class, and set the following properties for this object:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   The name of the published database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName).  
  
    -   A name for the publication for [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name).  
  
    -   A [PublicationType](assetId:///T:Microsoft.SqlServer.Replication.PublicationType) of either [Transactional](assetId:///F:Microsoft.SqlServer.Replication.PublicationType.Transactional) or [Snapshot](assetId:///F:Microsoft.SqlServer.Replication.PublicationType.Snapshot).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) fields of [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) to provide the credentials for the Windows account under which the Snapshot Agent runs. This account is also used when the Snapshot Agent makes connections to the local Distributor and for any remote connections when using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) is not required when the publication is created by a member of the **sysadmin** fixed server role. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) The [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [SnapshotGenerationAgentPublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity) when using SQL Server Authentication to connect to the Publisher.  
  
    -   \(Optional\) Use the inclusive logical OR operator \(**|** in Visual C\# and **Or** in Visual Basic\) and the exclusive logical OR operator \(**^** in Visual C\# and **Xor** in Visual Basic\) to set the [PublicationAttributes](assetId:///T:Microsoft.SqlServer.Replication.PublicationAttributes) values for the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property.  
  
    -   \(Optional\) The name of the Publisher for [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.TransPublication.PublisherName) when the Publisher is a non\-SQL Server Publisher.  
  
6.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method to create the publication.  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all properties, including [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity), are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before calling the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
7.  Call the [CreateSnapshotAgent](assetId:///M:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent) method to create the Snapshot Agent job for the publication.  
  
#### To create a merge publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationDatabase](assetId:///T:Microsoft.SqlServer.Replication.ReplicationDatabase) class for the publication database, set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the instance of [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1, and call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) returns **false**, verify that the database exists.  
  
3.  If [EnabledMergePublishing](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing) Property is **false**, set it to **true**, and call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges).  
  
4.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class, and set the following properties for this object:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   The name of the published database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName).  
  
    -   A name for the publication for [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) fields of [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) to provide the credentials for the Windows account under which the Snapshot Agent runs. This account is also used when the Snapshot Agent makes connections to the local Distributor and for any remote connections when using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) is not required when the publication is created by a member of the **sysadmin** fixed server role. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) Use the inclusive logical OR operator \(**|** in Visual C\# and **Or** in Visual Basic\) and the exclusive logical OR operator \(**^** in Visual C\# and **Xor** in Visual Basic\) to set the [PublicationAttributes](assetId:///T:Microsoft.SqlServer.Replication.PublicationAttributes) values for the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property.  
  
5.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method to create the publication.  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all properties, including [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity), are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before calling the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
6.  Call the [CreateSnapshotAgent](assetId:///M:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent) method to create the Snapshot Agent job for the publication.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example enables the AdventureWorks database for transactional publishing, defines a Log Reader Agent job, and creates the AdvWorksProductTran publication. An article must be defined for this publication. The Windows account credentials that are needed to create the Log Reader Agent job and the Snapshot Agent job are passed at runtime. To learn how to use RMO to define snapshot and transactional articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
 [!CODE [HowTo#rmo_CreateTranPub](../CodeSnippet/SQL15/replication/howto#rmo_createtranpub)]  
  
 [!CODE [HowTo#rmo_vb_CreateTranPub](../CodeSnippet/SQL15/replication/howto#rmo_vb_createtranpub)]  
  
 This example enables the AdventureWorks database for merge publishing and creates the AdvWorksSalesOrdersMerge publication. Articles must still be defined for this publication. The Windows account credentials that are needed to create the Snapshot Agent job are passed at runtime. To learn how to use RMO to define merge articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
 [!CODE [HowTo#rmo_CreateMergePub](../CodeSnippet/SQL15/replication/howto#rmo_createmergepub)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergePub](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergepub)]  
  
## See Also  
 [Use sqlcmd with Scripting Variables](../../Topics\TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md)   
 [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md)   
 [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md)  
  
  