---
title: Create a Push Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
---
# Create a Push Subscription
  This topic describes how to create a push subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\). For information about creating a push subscription for a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscriber, see [Create a Subscription for a Non-SQL Server Subscriber](../../Topics\TopicNameContainA/Create-a-Subscription-for-a-Non-SQL-Server-Subscriber.md).  
  
 **In This Topic**  
  
-   **To create a push subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Create a push subscription at the Publisher or the Subscriber using the New Subscription Wizard. Follow the pages in the wizard to:  
  
-   Specify the Publisher and publication.  
  
-   Select where replication agents will run. For a push subscription, select **Run all agents at the Distributor \(push subscriptions\)** on the **Distribution Agent Location** page or **Merge Agent Location** page, depending on the type of publication.  
  
-   Specify Subscribers and subscription databases.  
  
-   Specify the logins and passwords used for connections made by replication agents:  
  
    -   For subscriptions to snapshot and transactional publications, specify credentials on the **Distribution Agent Security** page.  
  
    -   For subscriptions to merge publications, specify credentials on the **Merge Agent Security** page.  
  
     For information about the permissions required by each agent, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
-   Specify a synchronization schedule and when the Subscriber should be initialized.  
  
-   Specify additional options for merge publications: subscription type; and values for parameterized filtering.  
  
-   Specify additional options for transactional publications that allow updating subscriptions: whether Subscribers should commit changes at the Publisher immediately or write them to a queue; credentials used to connect from the Subscriber to the Publisher.  
  
-   Optionally script the subscription.  
  
#### To create a push subscription from the Publisher  
  
1.  Connect to the Publisher in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Right\-click the publication for which you want to create one or more subscriptions, and then click **New Subscriptions**.  
  
4.  Complete the pages in the New Subscription Wizard.  
  
#### To create a push subscription from the Subscriber  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder.  
  
3.  Right\-click the **Local Subscriptions** folder, and then click **New Subscriptions**.  
  
4.  On the **Publication** page of the New Subscription Wizard, select **\<Find SQL Server Publisher\>** or **\<Find Oracle Publisher\>** from the **Publisher** drop\-down list.  
  
5.  Connect to the Publisher in the **Connect to Server** dialog box.  
  
6.  Select a publication on the **Publication** page.  
  
7.  Complete the pages in the New Subscription Wizard.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Push subscriptions can be created programmatically using replication stored procedures. The stored procedures used will depend on the type of publication to which the subscription belongs.  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at run time. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
#### To create a push subscription to a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, verify that the publication supports push subscriptions by executing [sp\_helppublication](../Topic/sp_helppublication%20\(Transact-SQL\).md).  
  
    -   If the value of **allow\_push** is **1**, push subscriptions are supported.  
  
    -   If the value of **allow\_push** is **0**, execute [sp\_changepublication](../Topic/sp_changepublication%20\(Transact-SQL\).md), specifying **allow\_push** for **@property** and **true** for **@value**.  
  
2.  At the Publisher on the publication database, execute [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md). Specify **@publication**, **@subscriber** and **@destination\_db**. Specify a value of **push** for **@subscription\_type**. For information about how to update subscriptions, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
3.  At the Publisher on the publication database, execute [sp\_addpushsubscription\_agent](../Topic/sp_addpushsubscription_agent%20\(Transact-SQL\).md). Specify the following:  
  
    -   The **@subscriber**, **@subscriber\_db**, and **@publication** parameters.  
  
    -   The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows credentials under which the Distribution Agent at the Distributor runs for **@job\_login** and **@job\_password**.  
  
        > [!NOTE]  
        >  Connections made using Windows Integrated Authentication always use the Windows credentials specified by **@job\_login** and **@job\_password**. The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication. By default, the agent will connect to the Subscriber using Windows Integrated Authentication.  
  
    -   \(Optional\) A value of **0** for **@subscriber\_security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@subscriber\_login** and **@subscriber\_password**. Specify these parameters if you need to use SQL Server Authentication when connecting to the Subscriber.  
  
    -   A schedule for the Distribution Agent job for this subscription. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
    > [!IMPORTANT]  
    >  When creating a push subscription at a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
#### To create a push subscription to a merge publication  
  
1.  At the Publisher on the publication database, verify that the publication supports push subscriptions by executing [sp\_helpmergepublication](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md).  
  
    -   If the value of **allow\_push** is **1**, the publication supports push subscriptions.  
  
    -   If the value of **allow\_push** is not **1**, execute [sp\_changemergepublication](../Topic/sp_changemergepublication%20\(Transact-SQL\).md), specifying **allow\_push** for **@property** and **true** for **@value**.  
  
2.  At the Publisher on the publication database, execute [sp\_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md), specifying the following parameters:  
  
    -   **@publication**. This is the name of the publication.  
  
    -   **@subscriber\_type**. For a client subscription, specify **local** and for a server subscription, specify **global**.  
  
    -   **@subscription\_priority**. For a server subscription, specify a priority for the subscription \(**0.00** to **99.99**\).  
  
         For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md).  
  
3.  At the Publisher on the publication database, execute [sp\_addmergepushsubscription\_agent](../Topic/sp_addmergepushsubscription_agent%20\(Transact-SQL\).md). Specify the following:  
  
    -   The **@subscriber**, **@subscriber\_db**, and **@publication** parameters.  
  
    -   The Windows credentials under which the Merge Agent at the Distributor runs for **@job\_login** and **@job\_password**.  
  
        > [!NOTE]  
        >  Connections made using Windows Integrated Authentication always use the Windows credentials specified by **@job\_login** and **@job\_password**. The Merge Agent always makes the local connection to the Distributor using Windows Integrated Authentication. By default, the agent will connect to the Subscriber using Windows Integrated Authentication.  
  
    -   \(Optional\) A value of **0** for **@subscriber\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@subscriber\_login** and **@subscriber\_password**. Specify these parameters if you need to use SQL Server Authentication when connecting to the Subscriber.  
  
    -   \(Optional\) A value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. Specify these values if you need to use SQL Server Authentication when connecting to the Publisher.  
  
    -   A schedule for the Merge Agent job for this subscription. For more information, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
    > [!IMPORTANT]  
    >  When creating a push subscription at a Publisher with a remote Distributor, the values supplied for all parameters, including *job\_login* and *job\_password*, are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before executing this stored procedure. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 The following example creates a push subscription to a transactional publication. Login and password values are supplied at run time by using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_addtranpushsubscription_agent](../CodeSnippet/SQL15/replication/howto#sp_addtranpushsubscription_agent)]  
  
 The following example creates a push subscription to a merge publication. Login and password values are supplied at run time by using **sqlcmd** scripting variables.  
  
 [!CODE [HowTo#sp_addmergepushsubscriptionagent](../CodeSnippet/SQL15/replication/howto#sp_addmergepushsubscriptionagent)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can create push subscriptions programmatically by using Replication Management Objects \(RMO\). The RMO classes you use to create a push subscription depend on the type of publication to which the subscription is created.  
  
> [!IMPORTANT]  
>  When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows .NET Framework.  
  
#### To create a push subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransPublication](assetId:///T:Microsoft.SqlServer.Replication.TransPublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName), and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 2 are incorrect or the publication does not exists on the server.  
  
4.  Perform a bitwise logical AND \(**&** in Visual C\# and **And** in Visual Basic\) between the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property and [AllowPush](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush). If the result is [None](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.None), set [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) to the result of a bitwise logical OR \(**|** in Visual C\# and **Or** in Visual Basic\) between [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) and [AllowPush](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush). Then, call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) to enable push subscriptions.  
  
5.  If the subscription database does not exist, create it by using the [Database](assetId:///T:Microsoft.SqlServer.Management.Smo.Database) class. For more information, see [Creating, Altering, and Removing Databases](../Topic/Creating,%20Altering,%20and%20Removing%20Databases.md).  
  
6.  Create an instance of the [TransSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransSubscription) class.  
  
7.  Set the following subscription properties:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) to the Publisher created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   Name of the subscription database for [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName).  
  
    -   Name of the Subscriber for [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName).  
  
    -   Name of the publication database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName).  
  
    -   Name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) or [SecurePassword](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword) fields of [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Distribution Agent runs at the Distributor. This account is used to make local connections to the Distributor and to make remote connections using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity) is not required when the subscription is created by a member of the **sysadmin** fixed server role, however it is recommended. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) A value of **true** \(the default\) for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault) to create an agent job that is used to synchronize the subscription. If you specify **false**, the subscription can only be synchronized programmatically.  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [SubscriberSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity) when using SQL Server Authentication to connect to the Subscriber.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Create) method.  
  
    > [!IMPORTANT]  
    >  When creating a push subscription at a Publisher with a remote Distributor, the values supplied for all properties, including [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity), are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before calling the [Create](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Create) method. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
#### To create a push subscription to a merge publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class by using the Publisher connection from step 1. Specify [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name), [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName), and [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method. If this method returns **false**, either the properties specified in step 2 are incorrect or the publication does not exists on the server.  
  
4.  Perform a bitwise logical AND \(**&** in Visual C\# and **And** in Visual Basic\) between the [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) property and [AllowPush](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush). If the result is [None](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.None), set [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) to the result of a bitwise logical OR \(**|** in Visual C\# and **Or** in Visual Basic\) between [Attributes](assetId:///P:Microsoft.SqlServer.Replication.Publication.Attributes) and [AllowPush](assetId:///F:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush). Then, call [CommitPropertyChanges](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges) to enable push subscriptions.  
  
5.  If the subscription database does not exist, create it by using the [Database](assetId:///T:Microsoft.SqlServer.Management.Smo.Database) class. For more information, see [Creating, Altering, and Removing Databases](../Topic/Creating,%20Altering,%20and%20Removing%20Databases.md).  
  
6.  Create an instance of the [MergeSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergeSubscription) class.  
  
7.  Set the following subscription properties:  
  
    -   The [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) to the Publisher created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
    -   Name of the subscription database for [SubscriptionDBName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName).  
  
    -   Name of the Subscriber for [SubscriberName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberName).  
  
    -   Name of the publication database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.DatabaseName).  
  
    -   Name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Subscription.PublicationName).  
  
    -   The [Login](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login) and [Password](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password) or [SecurePassword](assetId:///P:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword) fields of [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity) to provide the credentials for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Merge Agent runs at the Distributor. This account is used to make local connections to the Distributor and to make remote connections using Windows Authentication.  
  
        > [!NOTE]  
        >  Setting [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity) is not required when the subscription is created by a member of the **sysadmin** fixed server role, however it is recommended. In this case, the agent will impersonate the SQL Server Agent account. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    -   \(Optional\) A value of **true** \(the default\) for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault) to create an agent job that is used to synchronize the subscription. If you specify **false**, the subscription can only be synchronized programmatically.  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [SubscriberSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity) when using SQL Server Authentication to connect to the Subscriber.  
  
    -   \(Optional\) Set the [SqlStandardLogin](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin) and [SqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword) or [SecureSqlStandardPassword](assetId:///P:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword) fields of [PublisherSecurity](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity) when using SQL Server Authentication to connect to the Publisher.  
  
8.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Create) method.  
  
    > [!IMPORTANT]  
    >  When creating a push subscription at a Publisher with a remote Distributor, the values supplied for all properties, including [SynchronizationAgentProcessSecurity](assetId:///P:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity), are sent to the Distributor as plain text. You should encrypt the connection between the Publisher and its remote Distributor before calling the [Create](assetId:///M:Microsoft.SqlServer.Replication.Subscription.Create) method. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example creates a new push subscription to a transactional publication. The Windows account credentials you use to run the Distribution Agent job are passed at runtime.  
  
 [!CODE [HowTo#rmo_CreateTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_createtranpushsub)]  
  
 [!CODE [HowTo#rmo_vb_CreateTranPushSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_createtranpushsub)]  
  
 This example creates a new push subscription to a merge publication. The Windows account credentials you use to run the Merge Agent job are passed at runtime.  
  
 [!CODE [HowTo#rmo_CreateMergePushSub](../CodeSnippet/SQL15/replication/howto#rmo_createmergepushsub)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergePushSub](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergepushsub)]  
  
## See Also  
 [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)   
 [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)   
 [Use sqlcmd with Scripting Variables](../../Topics\TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md)  
  
  