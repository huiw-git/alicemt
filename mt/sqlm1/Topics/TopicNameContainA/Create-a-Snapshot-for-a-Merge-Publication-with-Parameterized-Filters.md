---
title: Create a Snapshot for a Merge Publication with Parameterized Filters
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
---
# Create a Snapshot for a Merge Publication with Parameterized Filters
  This topic describes how to create a snapshot for a merge publication with parameterized filters in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To create a snapshot for a merge publication with parameterized filters, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When generating a snapshot for a merge publication using parameterized filters, you must first generate a standard \(schema\) snapshot that contains all of the published data and Subscriber metadata for the subscription. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md). After you have created the schema snapshot, you can generate the snapshot that contains the Subscriber\-specific partition of the published data.  
  
-   If the filtering for one or more articles in the publication yields non\-overlapping partitions that are unique for each subscription, metadata is cleaned up whenever the Merge Agent runs. This means that the partitioned snapshot expires more quickly. When using this option, you should consider allowing Subscribers to initiate snapshot generation and delivery. For more information about filtering options, see the "Setting 'partition options'" section of [Snapshots for Merge Publications with Parameterized Filters](../../Topics\TopicNameNotContainA/Snapshots-for-Merge-Publications-with-Parameterized-Filters.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Generate snapshots for partitions on the **Data Partitions** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md). You can allow Subscribers to initiate snapshot generation and delivery and\/or generate snapshots.  
  
 Before generating snapshots for one or more partitions, you must:  
  
1.  Create a merge publication with the New Publication Wizard, and specify one or more parameterized row filters on the **Add Filter** page of the wizard. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
2.  Generate a schema snapshot for the publication. By default, a schema snapshot is generated when you complete the New Publication Wizard; you can also generate a schema snapshot from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
#### To generate a schema snapshot  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Publications** folder.  
  
3.  Right\-click the publication for which you want to create a snapshot, and then click **View Snapshot Agent Status**.  
  
4.  In the **View Snapshot Agent Status \- \<Publication\>** dialog box, click **Start**.  
  
     When the Snapshot Agent finishes generating the snapshot, a message will be displayed, such as "\[100%\] A snapshot of 17 article\(s\) was generated."  
  
#### To allow Subscribers to initiate snapshot generation and delivery  
  
1.  On the **Data Partitions** page of the **Publication Properties \- \<Publication\>** dialog box, select **Automatically define a partition and generate a snapshot if needed when a new Subscriber tries to synchronize**.  
  
2.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
#### To generate and refresh snapshots  
  
1.  On the **Data Partitions** page of the **Publication Properties \- \<Publication\>** dialog box, click **Add**.  
  
2.  Enter a value for the **HOST\_NAME\(\)** and\/or **SUSER\_SNAME\(\)** value associated with the partition for which you want to create a snapshot.  
  
3.  Optionally specify a schedule for refreshing snapshots:  
  
    1.  Select **Schedule the Snapshot Agent for this partition to run at the following time\(s\)**  
  
    2.  Accept the default schedule for refreshing snapshots, or click **Change** to specify a different schedule.  
  
4.  Click **OK**, which returns you to the **Publication Properties \- \<Publication\>** dialog box.  
  
5.  Select the partition in the property grid, and then click **Generate the selected snapshots now**.  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Using stored procedures and the Snapshot Agent, you can perform the following:  
  
-   Allow Subscribers to request snapshot generation and application the first time they synchronize.  
  
-   Pre\-generate snapshots for each partition.  
  
-   Manually generate a snapshot for each Subscriber.  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
#### To create a publication that allows Subscribers to initiate snapshot generation and delivery  
  
1.  At the Publisher on the publication database, execute [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md). Specify the following parameters:  
  
    -   The name of the publication for **@publication**.  
  
    -   A value of **true** for **@allow\_subscriber\_initiated\_snapshot**, which enables Subscribers to initiate the snapshot process.  
  
    -   \(Optional\) The number of dynamic snapshot processes that can run concurrently for **@max\_concurrent\_dynamic\_snapshots**. If the maximum number of processes is running and a Subscriber attempts to generate a snapshot, the process is placed in a queue. By default there is no limit to the number of concurrent processes.  
  
2.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 1 for **@publication** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows credentials under which the [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md) runs for **@job\_login** and **@password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication. For more information about generating an initial snapshot and defining a custom schedule for the Snapshot Agent, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
3.  Execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to add articles to the publication. This stored procedure must be executed once for each article in the publication. When using parameterized filters, you must specify a parameterized row filter for one or more articles using the **@subset\_filterclause** parameter. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
4.  If other articles will be filtered based on the parameterized row filter, execute [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md) to define the join or logical record relationships between articles. This stored procedure must be executed once for each relationship being defined. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
5.  When the Merge Agent requests the snapshot to initialize the Subscriber, the snapshot for the requesting subscription's partition is automatically generated.  
  
#### To create a publication and pre\-generate or automatically refresh snapshots  
  
1.  Execute [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md) to create the publication. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
2.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 1 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job\_login** and **@password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication. For more information about generating an initial snapshot and defining a custom schedule for the Snapshot Agent, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
3.  Execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to add articles to the publication. This stored procedure must be executed once for each article in the publication. When using parameterized filters, you must specify a parameterized row filter for one article using the **@subset\_filterclause** parameter. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
4.  If other articles will be filtered based on the parameterized row filter, execute [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md) to define the join or logical record relationships between articles. This stored procedure must be executed once for each relationship being defined. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
5.  At the Publisher on the publication database, execute [sp_helpmergepublication &#40;Transact-SQL&#41;](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md), specifying the value of **@publication** from step 1. Note the value of the **snapshot\_jobid** in the result set.  
  
6.  Convert the value of the **snapshot\_jobid** obtained in step 5 to **uniqueidentifier**.  
  
7.  At the Publisher on the **msdb** database, execute [sp_start_job &#40;Transact-SQL&#41;](../Topic/sp_start_job%20\(Transact-SQL\).md), specifying the converted value obtained in step 6 for **@job\_id**.  
  
8.  At the Publisher on the publication database, execute [sp_addmergepartition &#40;Transact-SQL&#41;](../Topic/sp_addmergepartition%20\(Transact-SQL\).md). Specify the name of the publication from step 1 for **@publication** and the value used to define the partition for **@suser\_sname** if [SUSER_SNAME &#40;Transact-SQL&#41;](../Topic/SUSER_SNAME%20\(Transact-SQL\).md) is used in the filter clause or for **@host\_name** if [HOST_NAME &#40;Transact-SQL&#41;](../Topic/HOST_NAME%20\(Transact-SQL\).md) is used in the filter clause.  
  
9. At the publisher on the publication database, execute [sp_adddynamicsnapshot_job &#40;Transact-SQL&#41;](../Topic/sp_adddynamicsnapshot_job%20\(Transact-SQL\).md). Specify the name of the publication from step 1 for **@publication**, the value of **@suser\_sname** or **@host\_name** from step 8, and a schedule for the job. This creates the job that generates the parameterized snapshot for the specified partition. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
    > [!NOTE]  
    >  This job runs using the same Windows account as the initial snapshot job defined in step 2. To remove the parameterized snapshot job and its related data partition, execute [sp_dropdynamicsnapshot_job &#40;Transact-SQL&#41;](../Topic/sp_dropdynamicsnapshot_job%20\(Transact-SQL\).md).  
  
10. At the Publisher on the publication database, execute [sp_helpmergepartition &#40;Transact-SQL&#41;](../Topic/sp_helpmergepartition%20\(Transact-SQL\).md), specifying the value of **@publication** from step 1 and the value of **@suser\_sname** or **@host\_name** from step 8. Note the value of the **dynamic\_snapshot\_jobid** in the result set.  
  
11. At the Distributor on the **msdb** database, execute [sp_start_job &#40;Transact-SQL&#41;](../Topic/sp_start_job%20\(Transact-SQL\).md), specifying the value obtained in step 9 for **@job\_id**. This starts the parameterized snapshot job for the partition.  
  
12. Repeat steps 8\-11 to generate a partitioned snapshot for each subscription.  
  
#### To create a publication and manually create snapshots for each partition  
  
1.  Execute [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md) to create the publication. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
2.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 1 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job\_login** and **@password**. If the agent will use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication. For more information about generating an initial snapshot and defining a custom schedule for the Snapshot Agent, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
3.  Execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to add articles to the publication. This stored procedure must be executed once for each article in the publication. When using parameterized filters, you must specify a parameterized row filter for at least one article using the **@subset\_filterclause** parameter. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
4.  If other articles will be filtered based on the parameterized row filter, execute [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md) to define the join or logical record relationships between articles. This stored procedure must be executed once for each relationship being defined. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
5.  Start the snapshot job or run the Replication Snapshot Agent from the command prompt to generate the standard snapshot schema and other files. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
6.  Run the Replication Snapshot Agent again from the command prompt to generate bulk copy \(.bcp\) files, specifying the location of the partitioned snapshot for **\-DynamicSnapshotLocation** and one or both of the following properties that defines the partition:  
  
    -   **\-DynamicFilterHostName** \- the value if [HOST_NAME &#40;Transact-SQL&#41;](../Topic/HOST_NAME%20\(Transact-SQL\).md) is used.  
  
    -   **\-DynamicFilterLogin** \- the value if [SUSER_SNAME &#40;Transact-SQL&#41;](../Topic/SUSER_SNAME%20\(Transact-SQL\).md) is used.  
  
7.  Repeat step 6 to generate a partitioned snapshot for each subscription.  
  
8.  Run the Merge Agent for each subscription to apply the initial partitioned snapshot at the Subscribers, specifying the following properties:  
  
    -   **\-Hostname** \- the value used to define the partition if the actual value of HOST\_NAME is being overridden.  
  
    -   **\-DynamicSnapshotLocation** \- the location of the dynamic snapshot for this partition.  
  
> [!NOTE]  
>  For more information about programming replication agents, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example creates a merge publication with parameterized filters where Subscribers initiate the snapshot generation process. Values for **@job\_login** and **@job\_password** are passed in using scripting variables.  
  
 [!CODE [HowTo#sp_MergeDynamicPub1](../CodeSnippet/SQL15/replication/howto#sp_mergedynamicpub1)]  
  
 This example creates a publication using a parameterized filter where each Subscriber has its partition defined by executing [sp\_addmergepartition](../Topic/sp_addmergepartition%20\(Transact-SQL\).md) and the filtered snapshot job created by executing [sp\_adddynamicsnapshot\_job](../Topic/sp_adddynamicsnapshot_job%20\(Transact-SQL\).md) passing the partitioning information. Values for **@job\_login** and **@job\_password** are passed in using scripting variables.  
  
 [!CODE [HowTo#sp_MergeDynamicPubPlusPartition](../CodeSnippet/SQL15/replication/howto#sp_mergedynamicpubpluspartition)]  
  
 This example creates a publication using a parameterized filter where each Subscriber must have its data partition and filtered snapshot job created by supplying the partitioning information. A Subscriber supplies partitioning information using command\-line parameters when manually running the replication agents. This example assumes that a subscription to the publication has also been created.  
  
 [!CODE [HowTo#sp_MergeDynamicPubPartitionManual](../CodeSnippet/SQL15/replication/howto#sp_mergedynamicpubpartitionmanual)]  
  
```  
  
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
  
```  
  
```  
  
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
```  
  
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can use Replication Management Objects \(RMO\) to generate partitioned snapshots programmatically in the following ways:  
  
-   Allow Subscribers to request snapshot generation and application the first time they synchronize.  
  
-   Pre\-generate snapshots for each partition.  
  
-   Manually generate a snapshot for each Subscriber by running the Snapshot Agent.  
  
> [!NOTE]  
>  When filtering for an article yields non\-overlapping partitions that are unique for each subscription \(by specifying a value of F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription for P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption when creating a merge article\), metadata is cleaned up whenever the Merge Agent runs. This means that the partitioned snapshot expires more quickly. When you use this option, you should consider allowing Subscribers to request snapshot generation. For more information, see the section Using the Appropriate Filtering Options in the topic [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows .NET Framework.  
  
#### To create a publication that allows Subscribers to initiate snapshot generation and delivery  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationDatabase](assetId:///T:Microsoft.SqlServer.Replication.ReplicationDatabase) class for the publication database, set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the instance of [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1, and call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) returns **false**, confirm that the database exists.  
  
3.  If [EnabledMergePublishing](assetId:///P:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing) property is **false**, set it to **true** and call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges).  
  
4.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class, and set the following properties for this object:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   The name of the published database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName).  
  
    -   A name for the publication for [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name).  
  
    -   The maximum number of dynamic snapshot jobs to run for [MaxConcurrentDynamicSnapshots](assetId:///P:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots). Because Subscriber initiated snapshot requests can occur at any time, this property limits the number of Snapshot Agent jobs that can run simultaneously when multiple Subscribers request their partitioned snapshot at the same time. When the maximum number of jobs are running, additional partitioned snapshot requests are queued until one of the running jobs is completed.  
  
    -   Use the bitwise logical OR \(**|** in Visual C\# and **Or** in Visual Basic\) operator to add the value [AllowSubscriberInitiatedSnapshot](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot) to [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) fields of [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Snapshot Agent job runs.  
  
        > [!NOTE]  
        >  Setting [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity) is recommended when the publication is created by a member of the **sysadmin** fixed server role. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
5.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method to create the publication.  
  
    > [!IMPORTANT]  
    >  When configuring a Publisher with a remote Distributor, the values supplied for all properties, including [SnapshotGenerationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity), are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before calling the [Create](assetId:///M:Microsoft.SqlServer.Replication.Publication.Create) method. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
6.  Use the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) property to add articles to the publication. Specify the [FilterClause](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.FilterClause) property for at least one article that defines the parameterized filter. \(Optional\) Create [MergeJoinFilter](assetId:///T:Microsoft.SqlServer.Replication.MergeJoinFilter) objects that define join filters between articles. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
7.  If the value of [SnapshotAgentExists](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists) is **false**, call [CreateSnapshotAgent](assetId:///M:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent) to create the initial Snapshot Agent job for this publication.  
  
8.  Call the [StartSnapshotGenerationAgentJob](assetId:///M:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob) method of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) object created in step 4. This starts the agent job that generates the initial snapshot. For more information about generating an initial snapshot and defining a custom schedule for the Snapshot Agent, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
9. \(Optional\) Check for a value of **true** for the [SnapshotAvailable](assetId:///P:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable) property to determine when the initial snapshot is ready for use.  
  
10. When the Merge Agent for a Subscriber connects for the first time, a partitioned snapshot is generated automatically.  
  
#### To create a publication and pregenerate or automatically refresh snapshots  
  
1.  Use an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class to define a merge publication. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
2.  Use the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) property to add articles to the publication. Specify the [FilterClause](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.FilterClause) property for at least one article that defines the parameterized filter, and create any [MergeJoinFilter](assetId:///T:Microsoft.SqlServer.Replication.MergeJoinFilter) objects that define join filters between articles. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
3.  If the value of [SnapshotAgentExists](assetId:///P:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists) is **false**, call [CreateSnapshotAgent](assetId:///M:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent) to create the snapshot agent job for this publication.  
  
4.  Call the [StartSnapshotGenerationAgentJob](assetId:///M:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob) method of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) object created in step 1. This method starts the agent job that generates the initial snapshot. For more information on generating an initial snapshot and defining a custom schedule for the Snapshot Agent, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
5.  Check for a value of **true** for the [SnapshotAvailable](assetId:///P:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable) property to determine when the initial snapshot is ready for use.  
  
6.  Create an instance of the [MergePartition](assetId:///T:Microsoft.SqlServer.Replication.MergePartition) class, and set the parameterized filtering criteria for the Subscriber by using one or both of the following properties:  
  
    -   If the Subscriber's partition is defined by the result of [SUSER_SNAME &#40;Transact-SQL&#41;](../Topic/SUSER_SNAME%20\(Transact-SQL\).md), use [DynamicFilterLogin](assetId:///P:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin).  
  
    -   If the Subscriber's partition is defined by the result of [HOST_NAME &#40;Transact-SQL&#41;](../Topic/HOST_NAME%20\(Transact-SQL\).md) or an overload of this function, use [DynamicFilterHostName](assetId:///P:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName).  
  
7.  Create an instance of the [MergeDynamicSnapshotJob](assetId:///T:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob) class, and set the same property as in step 6.  
  
8.  Use the [ReplicationAgentSchedule](assetId:///T:Microsoft.SqlServer.Replication.ReplicationAgentSchedule) class to define a schedule for generating the filtered snapshot for the Subscriber partition.  
  
9. Using the instance of [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) from step 1, call [AddMergePartition](assetId:///M:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition(Microsoft.SqlServer.Replication.MergePartition)). Pass the [MergePartition](assetId:///T:Microsoft.SqlServer.Replication.MergePartition) object from step 6.  
  
10. Using the instance of [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) from step 1, call the [AddMergeDynamicSnapshotJob](assetId:///M:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob(Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob,Microsoft.SqlServer.Replication.ReplicationAgentSchedule)) method. Pass the [MergeDynamicSnapshotJob](assetId:///T:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob) object from step 7 and the [ReplicationAgentSchedule](assetId:///T:Microsoft.SqlServer.Replication.ReplicationAgentSchedule) object from step 8.  
  
11. Call [EnumMergeDynamicSnapshotJobs](assetId:///M:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs), and locate the [MergeDynamicSnapshotJob](assetId:///T:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob) object for the newly added partitioned snapshot job in the returned array.  
  
12. Get the [Name](assetId:///P:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name) property for the job.  
  
13. Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
14. Create an instance of the SQL Server Management Objects \(SMO\) [Server](assetId:///T:Microsoft.SqlServer.Management.Smo.Server) class, passing the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) object from step 13.  
  
15. Create an instance of the [Job](assetId:///T:Microsoft.SqlServer.Management.Smo.Agent.Job) class, passing the [JobServer](assetId:///P:Microsoft.SqlServer.Management.Smo.Server.JobServer) property of the [Server](assetId:///T:Microsoft.SqlServer.Management.Smo.Server) object from step 14 and the job name from step 12.  
  
16. Call the [Start](assetId:///M:Microsoft.SqlServer.Management.Smo.Agent.Job.Start) method to start the partitioned snapshot job.  
  
17. Repeat steps 6\-16 for each Subscriber.  
  
#### To create a publication and manually create snapshots for each partition  
  
1.  Use an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class to define a merge publication. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
2.  Use the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) property to add articles to the publication Specify the [FilterClause](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.FilterClause) property for at least one article that defines the parameterized filter, and create any [MergeJoinFilter](assetId:///T:Microsoft.SqlServer.Replication.MergeJoinFilter) objects that define join filters between articles. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
3.  Generate the initial snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
4.  Create an instance of the [T:Microsoft.SqlServer.Replication.SnapshotGenerationAgent](assetId:///T:Microsoft.SqlServer.Replication.SnapshotGenerationAgent) class, and set the following required properties:  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher) \- name of the Publisher  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase) \- name of the publication database  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication) \- name of the publication  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor) \- name of the Distributor  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode) \- a value of [Integrated](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Integrated) to used Windows Integrated Authentication or a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) to use SQL Server Authentication.  
  
    -   [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode) \- a value of [Integrated](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Integrated) to used Windows Integrated Authentication or a value of [Standard](assetId:///F:Microsoft.SqlServer.Replication.SecurityMode.Standard) to use SQL Server Authentication.  
  
5.  Set a value of [Merge](assetId:///F:Microsoft.SqlServer.Replication.ReplicationType.Merge) for [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType).  
  
6.  Set one or more of the following properties to define the partitioning parameters:  
  
    -   If the Subscriber's partition is defined by the result of [SUSER_SNAME &#40;Transact-SQL&#41;](../Topic/SUSER_SNAME%20\(Transact-SQL\).md), use [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin).  
  
    -   If the Subscriber's partition is defined by the result of [HOST_NAME &#40;Transact-SQL&#41;](../Topic/HOST_NAME%20\(Transact-SQL\).md) or an overload of this function, use [P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName](assetId:///P:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName).  
  
7.  Call the [M:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot](assetId:///M:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot) method.  
  
8.  Repeat steps 4\-7 for each Subscriber.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example creates a merge publication that allows Subscribers to requested snapshot generation.  
  
 [!CODE [HowTo#rmo_CreateMergePub](../CodeSnippet/SQL15/replication/howto#rmo_createmergepub)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergePub](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergepub)]  
  
 This example manually creates the Subscriber partition and the filtered snapshot for a merge publication with parameterized row filters.  
  
 [!CODE [HowTo#rmo_CreateMergePartition](../CodeSnippet/SQL15/replication/howto#rmo_createmergepartition)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergePartition](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergepartition)]  
  
 This example manually starts the Snapshot Agent to generate the filtered data snapshot for a Subscriber to a merge publication with parameterized row filters.  
  
 [!CODE [HowTo#rmo_GenerateFilteredSnapshot](../CodeSnippet/SQL15/replication/howto#rmo_generatefilteredsnapshot)]  
  
 [!CODE [HowTo#rmo_vb_GenerateFilteredSnapshot](../CodeSnippet/SQL15/replication/howto#rmo_vb_generatefilteredsnapshot)]  
  
## See Also  
 [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../Topics\TopicNameNotContainA/Snapshots-for-Merge-Publications-with-Parameterized-Filters.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  