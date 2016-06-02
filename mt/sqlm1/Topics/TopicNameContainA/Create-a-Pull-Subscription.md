---
title: Create a Pull Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
---
# Create a Pull Subscription
  This topic describes how create a pull subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 Setting up a pull subscription for P2P replication is possible by script, but is not available through the wizard.  
  
 **In This Topic**  
  
-   **To create a pull subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Create a pull subscription at the Publisher or the Subscriber using the New Subscription Wizard. Follow the pages in the wizard to:  
  
-   Specify the Publisher and publication.  
  
-   Select where replication agents will run. For a pull subscription, select **Run each agent at its Subscriber \(pull subscriptions\)** on the **Distribution Agent Location** page or **Merge Agent Location** page, depending on the type of publication.  
  
-   Specify Subscribers and subscription databases.  
  
-   Specify the logins and passwords used for connections made by replication agents:  
  
    -   For subscriptions to snapshot and transactional publications, specify credentials on the **Distribution Agent Security** page.  
  
    -   For subscriptions to merge publications, specify credentials on the **Merge Agent Security** page.  
  
     For information about the permissions required by each agent, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
-   Specify a synchronization schedule and when the Subscriber should be initialized.  
  
-   Specify additional options for merge publications: subscription type; values for parameterized filtering; and information for synchronization through HTTPS if the publication is enabled for Web synchronization.  
  
-   Specify additional options for transactional publications that allow updating subscriptions: whether Subscribers should commit changes at the Publisher immediately or write them to a queue; credentials used to connect from the Subscriber to the Publisher.  
  
-   Optionally script the subscription.  
  
#### To create a pull subscription from the Publisher  
  
1.  Connect to the Publisher in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Right\-click the publication for which you want to create one or more subscriptions, and then click **New Subscriptions**.  
  
4.  Complete the pages in the New Subscription Wizard.  
  
#### To create a pull subscription from the Subscriber  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder.  
  
3.  Right\-click the **Local Subscriptions** folder, and then click **New Subscriptions**.  
  
4.  On the **Publication** page of the New Subscription Wizard, select **\<Find SQL Server Publisher\>** or **\<Find Oracle Publisher\>** from the **Publisher** drop\-down list.  
  
5.  Connect to the Publisher in the **Connect to Server** dialog box.  
  
6.  Select a publication on the **Publication** page.  
  
7.  Complete the pages in the New Subscription Wizard.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Pull subscriptions can be created programmatically using replication stored procedures. The stored procedures used will depend on the type of publication to which the subscription belongs.  
  
#### To create a pull subscription to a snapshot or transactional publication  
  
1.  At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication &#40;Transact-SQL&#41;](../Topic/sp_helppublication%20\(Transact-SQL\).md).  
  
    -   If the value of **allow\_pull** in the result set is **1**, then the publication supports pull subscriptions.  
  
    -   If the value of **allow\_pull** is **0**, execute [sp_changepublication &#40;Transact-SQL&#41;](../Topic/sp_changepublication%20\(Transact-SQL\).md), specifying **allow\_pull** for **@property** and **true** for **@value**.  
  
2.  At the Subscriber, execute [sp_addpullsubscription &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription%20\(Transact-SQL\).md). Specify **@publisher** and **@publication**. For information about updating subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
3.  At the Subscriber, execute [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addpullsubscription_agent%20\(Transact-SQL\).md). Specify the following:  
  
    -   The **@publisher**, **@publisher\_db**, and **@publication** parameters.  
  
    -   The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job\_login** and **@job\_password**.  
  
        > [!NOTE]  
        >  Connections made using Windows Integrated Authentication always use the Windows credentials specified by **@job\_login** and **@job\_password**. The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication. By default, the agent will connect to the Distributor using Windows Integrated Authentication.  
  
    -   \(Optional\) A value of **0** for **@distributor\_security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@distributor\_login** and **@distributor\_password**, if you need to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Distributor.  
  
    -   A schedule for the Distribution Agent job for this subscription. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
4.  At the Publisher, execute [sp_addsubscription &#40;Transact-SQL&#41;](../Topic/sp_addsubscription%20\(Transact-SQL\).md) to register the pull subscription. Specify **@publication**, **@subscriber**, and **@destination\_db**. Specify a value of **pull** for **@subscription\_type**.  
  
#### To create a pull subscription to a merge publication  
  
1.  At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helpmergepublication &#40;Transact-SQL&#41;](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md).  
  
    -   If the value of **allow\_pull** in the result set is **1**, then the publication supports pull subscriptions.  
  
    -   If the value of **allow\_pull** is **0**, execute [sp_changemergepublication &#40;Transact-SQL&#41;](../Topic/sp_changemergepublication%20\(Transact-SQL\).md), specifying **allow\_pull** for **@property** and **true** for **@value**.  
  
2.  At the Subscriber, execute [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../Topic/sp_addmergepullsubscription%20\(Transact-SQL\).md). Specify **@publisher**, **@publisher\_db**, **@publication**, and the following parameters:  
  
    -   **@subscriber\_type** – specify **local** for a client subscription and **global** for a server subscription.  
  
    -   **@subscription\_priority** – Specify a priority for the subscription \(**0.00** to **99.99**\). This is only required for a server subscription.  
  
         For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md).  
  
3.  At the Subscriber, execute [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md). Specify the following parameters:  
  
    -   **@publisher**, **@publisher\_db**, and **@publication**.  
  
    -   The Windows credentials under which the Merge Agent at the Subscriber runs for **@job\_login** and **@job\_password**.  
  
        > [!NOTE]  
        >  Connections made using Windows Integrated Authentication always use the Windows credentials specified by **@job\_login** and **@job\_password**. The Merge Agent always makes the local connection to the Subscriber using Windows Integrated Authentication. By default, the agent will connect to the Distributor and Publisher using Windows Integrated Authentication.  
  
    -   \(Optional\) A value of **0** for **@distributor\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@distributor\_login** and **@distributor\_password**, if you need to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Distributor.  
  
    -   \(Optional\) A value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**, if you need to use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication when connecting to the Publisher.  
  
    -   A schedule for the Merge Agent job for this subscription. For more information, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
4.  At the Publisher, execute [sp_addmergesubscription &#40;Transact-SQL&#41;](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber**, **@subscriber\_db**, and a value of **pull** for **@subscription\_type**. This registers the pull subscription.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 The following example creates a pull subscription to a transactional publication. The first batch is executed at the Subscriber, and the second batch is executed at the Publisher. Login and password values are supplied at runtime using sqlcmd scripting variables.  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
  
-- At the subscription database, create a pull subscription   
-- to a transactional publication.  
USE [AdventureWorksReplica]  
EXEC sp_addpullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.  
EXEC sp_addpullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password);  
GO  
```  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Publisher.  
DECLARE @publication AS sysname;  
DECLARE @subscriber AS sysname;  
DECLARE @subscriptionDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @subscriber = $(SubServer);  
SET @subscriptionDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
EXEC sp_addsubscription   
  @publication = @publication,   
  @subscriber = @subscriber,   
  @destination_db = @subscriptionDB,   
  @subscription_type = N'pull',  
  @status = N'subscribed';  
GO  
  
```  
  
 The following example creates a pull subscription to a merge publication. The first batch is executed at the Subscriber, and the second batch is executed at the Publisher. Login and password values are supplied at runtime using **sqlcmd** scripting variables.  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
DECLARE @hostname AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
SET @hostname = N'adventure-works\david8';  
  
-- At the subscription database, create a pull subscription   
-- to a merge publication.  
USE [AdventureWorksReplica]  
EXEC sp_addmergepullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.   
EXEC sp_addmergepullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password),  
  @hostname = @hostname;  
GO  
```  
  
```  
-- Execute this batch at the Publisher.  
DECLARE @myMergePub  AS sysname;  
DECLARE @mySub       AS sysname;  
DECLARE @mySubDB     AS sysname;  
  
SET @myMergePub = N'AdvWorksSalesOrdersMerge';  
SET @mySub = N'MYSUBSERVER';  
SET @mySubDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
USE [AdventureWorks]  
EXEC sp_addmergesubscription @publication = @myMergePub,   
@subscriber = @mySub, @subscriber_db = @mySubDB,   
@subscription_type = N'pull';  
GO  
```  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 The RMO classes used to create a pull subscription depend on the type of publication to which the subscription belongs.  
  
#### To create a pull subscription to a snapshot or transactional publication  
  
1.  Create connections to both the Subscriber and Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) Class.  
  
2.  Create an instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 2 are incorrect or the publication does not exist on the server.  
  
4.  Perform a bitwise logical AND \(**&** in Visual C\# and **And** in Visual Basic\) between the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property and [AllowPull](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull). If the result is [None](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.None), set [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) to the result of a bitwise logical OR \(**|** in Visual C\# and **Or** in Visual Basic\) between [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) and [AllowPull](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull). Then, call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) to enable pull subscriptions.  
  
5.  If the subscription database does not exist, create it by using the [Database](assetId:///T:Microsoft.SqlServer.Management.Smo.Database) class. For more information, see [Creating, Altering, and Removing Databases](../Topic/Creating,%20Altering,%20and%20Removing%20Databases.md).  
  
6.  Create an instance of the [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) class.  
  
7.  Set the following subscription properties:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) to the Subscriber created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   Name of the subscription database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName).  
  
    -   Name of the Publisher for [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName).  
  
    -   Name of the publication database for [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName).  
  
    -   Name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) or [SecurePassword](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword) fields of [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Distribution Agent runs at the Subscriber. This account is used to make local connections to the Subscriber and to make remote connections using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity) is not required when the subscription is created by a member of the **sysadmin** fixed server role, however it is recommended. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) A value of **true** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) to create an agent job that is used to synchronize the subscription. If you specify **false** \(the default\), the subscription can only be synchronized programmatically and you must specify additional properties of [TransSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.TransSynchronizationAgent) when you access this object from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent) property. For more information, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
        > [!NOTE]  
        >  SQL Server Agent is not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md). When you specify a value of **true** for Express Subscribers, the agent job is not created. However, important subscription\-related metadata is stored at the Subscriber.  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [DistributorSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity) when using SQL Server Authentication to connect to the Distributor.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.PullSubscription.Create) method.  
  
9. Using the instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class from step 2, call the [MakePullSubscriptionWellKnown](assetId:///M:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown(System.String,System.String,Microsoft.SqlServer.Replication.SubscriptionSyncType,Microsoft.SqlServer.Replication.TransSubscriberType)) method to register the pull subscription with the Publisher. If this registration already exists, an exception occurs.  
  
#### To create a pull subscription to a merge publication  
  
1.  Create connections to both the Subscriber and Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName), and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 2 are incorrect or the publication does not exist on the server.  
  
4.  Perform a bitwise logical AND \(**&** in Visual C\# and **And** in Visual Basic\) between the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property and [AllowPull](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull). If the result is [None](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.None), set [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) to the result of a bitwise logical OR \(**|** in Visual C\# and **Or** in Visual Basic\) between [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) and [AllowPull](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull). Then, call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) to enable pull subscriptions.  
  
5.  If the subscription database does not exist, create it by using the [Database](assetId:///T:Microsoft.SqlServer.Management.Smo.Database) class. For more information, see [Creating, Altering, and Removing Databases](../Topic/Creating,%20Altering,%20and%20Removing%20Databases.md).  
  
6.  Create an instance of the [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) class.  
  
7.  Set the following subscription properties:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) to the Subscriber created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   Name of the subscription database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName).  
  
    -   Name of the Publisher for [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName).  
  
    -   Name of the publication database for [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName).  
  
    -   Name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) or [SecurePassword](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword) fields of [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Merge Agent runs at the Subscriber. This account is used to make local connections to the Subscriber and to make remote connections using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity) is not required when the subscription is created by a member of the **sysadmin** fixed server role, however it is recommended. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) A value of **true** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) to create an agent job that is used to synchronize the subscription. If you specify **false** \(the default\), the subscription can only be synchronized programmatically and you must specify additional properties of [MergeSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.MergeSynchronizationAgent) when you access this object from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent) property. For more information, see [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md).  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [DistributorSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity) when using SQL Server Authentication to connect to the Distributor.  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [PublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity) when using SQL Server Authentication to connect to the Publisher.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.PullSubscription.Create) method.  
  
9. Using the instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class from step 2, call the [MakePullSubscriptionWellKnown](assetId:///M:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown(System.String,System.String,Microsoft.SqlServer.Replication.SubscriptionSyncType,Microsoft.SqlServer.Replication.MergeSubscriberType,System.Single)) method to register the pull subscription with the Publisher. If this registration already exists, an exception occurs.  
  
###  <a name="PShellExample"></a> Example \(RMO\)  
 This example creates a pull subscription to a transactional publication. The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account credentials used to create the Distribution Agent job are passed at runtime.  
  
```c#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksProductTran";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
TransPublication publication;  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Publisher and Subscriber.  
    subscriberConn.Connect();  
    publisherConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new TransPublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.IsExistingObject)  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new TransPullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // By default, subscriptions to transactional publications are synchronized   
        // continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (TransSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                TransSubscriberType.ReadOnly);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksProductTran"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As TransPublication  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Publisher and Subscriber.  
    subscriberConn.Connect()  
    publisherConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New TransPublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.IsExistingObject Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New TransPullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.Description = "Pull subscription to " + publicationDbName _  
        + " on " + subscriberName + "."  
  
        ' Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' By default, subscriptions to transactional publications are synchronized   
        ' continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As TransSubscription In publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName And _  
                existing.SubscriptionDBName = subscriptionDbName Then  
                registered = True  
            End If  
        Next existing  
        If Not registered Then  
            ' Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             TransSubscriberType.ReadOnly)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
  
```  
  
 This example creates a pull subscription to a merge publication. The Windows account credentials used to create the Merge Agent job are passed at runtime.  
  
```cpp#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 This example creates a pull subscription to a merge publication without creating an associated agent job and subscription metadata in [MSsubscription\_properties](../Topic/MSsubscription_properties%20\(Transact-SQL\).md). The Windows account credentials used to create the Merge Agent job are passed at runtime.  
  
```c#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify that an agent job not be created for this subscription. The  
        // subscription can only be synchronized by running the Merge Agent directly.  
        // Subscripition metadata stored in MSsubscription_properties will not  
        // be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = false;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
  
        ' Specify that an agent job not be created for this subscription. The  
        ' subscription can only be synchronized by running the Merge Agent directly.  
        ' Subscripition metadata stored in MSsubscription_properties will not  
        ' be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = False  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 This example creates a pull subscription to a merge publication that can be synchronized over the Internet using Web synchronization. The Windows account credentials used to create the Merge Agent job are passed at runtime. For more information, see [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md).  
  
```c#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
string webSyncUrl = "https://" + publisherInstance + "/WebSync/replisapi.dll";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions and Web synchronization.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
        if ((publication.Attributes & PublicationAttributes.AllowWebSynchronization) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowWebSynchronization;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Enable Web synchronization.  
        subscription.UseWebSynchronization = true;  
        subscription.InternetUrl = webSyncUrl;  
  
        // Specify the same Windows credentials to use when connecting to the  
        // Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication;  
        subscription.InternetLogin = winLogin;  
        subscription.InternetPassword = winPassword;  
  
        // Ensure that we create a job for this subscription.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
Dim webSyncUrl As String = "https://" + publisherInstance + "/WebSync/replisapi.dll"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions and Web synchronization.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
        If (publication.Attributes And PublicationAttributes.AllowWebSynchronization) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowWebSynchronization  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Enable Web synchronization.  
        subscription.UseWebSynchronization = True  
        subscription.InternetUrl = webSyncUrl  
  
        ' Specify the same Windows credentials to use when connecting to the  
        ' Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication  
        subscription.InternetLogin = winLogin  
        subscription.InternetPassword = winPassword  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
## See Also  
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)   
 [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  