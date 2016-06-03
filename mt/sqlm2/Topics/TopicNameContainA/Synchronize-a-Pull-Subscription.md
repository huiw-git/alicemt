---
title: Synchronize a Pull Subscription
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
---
# Synchronize a Pull Subscription
  This topic describes how to synchronize a pull subscription in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [replication agents](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md), or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **To synchronize a pull subscription, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Replication Agents](#ReplProg)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Subscriptions are synchronized by the Distribution Agent \(for snapshot and transactional replication\) or the Merge Agent \(for merge replication\). Agents can run continuously, run on demand, or run on a schedule. For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](../../Topics\TopicNameNotContainA/Specify-Synchronization-Schedules.md).  
  
 Synchronize a subscription on demand from the **Local Subscriptions** folder in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
#### To synchronize a pull subscription on demand in Management Studio  
  
1.  Connect to the Subscriber in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.  
  
3.  Right\-click the subscription you want to synchronize, and then click **View Synchronization Status**.  
  
4.  In the **View Synchronization Status \- \<Subscriber\>:\<SubscriptionDatabase\>** dialog box, click **Start**. When synchronization is complete, the message **Synchronization completed** is displayed.  
  
5.  Click **Close**.  
  
##  <a name="ReplProg"></a> Replication Agents  
 Pull subscriptions can be synchronized programmatically and on\-demand by invoking the appropriate replication agent executable file from the command prompt. The replication agent executable file that is invoked will depend on the type of publication to which the pull subscription belongs. For more information, see [Replication Agents](../../Topics\TopicNameNotContainA/Replication-Agents.md).  
  
> [!NOTE]  
>  Replication agents connect to the local server using the Windows Authentication credentials of the user who started the agent from the command prompt. These Windows credentials are also used when connecting to remote servers using Windows Integrated Authentication.  
  
#### To start the distribution agent from the command prompt or from a batch file  
  
1.  From the command prompt or in a batch file, start the [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md) by running **distrib.exe**, specifying the following command\-line arguments:  
  
    -   **\-Publisher**  
  
    -   **\-PublisherDB**  
  
    -   **\-Distributor**  
  
    -   **\-DistributorSecurityMode** \= **1**  
  
    -   **\-Subscriber**  
  
    -   **\-SubscriberDB**  
  
    -   **\-SubscriberSecurityMode** \= **1**  
  
    -   **\-SubscriptionType** \= **1**  
  
     If you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must also specify the following arguments:  
  
    -   **\-DistributorLogin**  
  
    -   **\-DistributorPassword**  
  
    -   **\-DistributorSecurityMode** \= **0**  
  
    -   **\-PublisherLogin**  
  
    -   **\-PublisherPassword**  
  
    -   **\-PublisherSecurityMode** \= **0**  
  
    -   **\-SubscriberLogin**  
  
    -   **\-SubscriberPassword**  
  
    -   **\-SubscriberSecurityMode** \= **0**  
  
#### To start the merge agent from the command prompt or from a batch file  
  
1.  From the command prompt or in a batch file, start the [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md) by running **replmerg.exe**, specifying the following command\-line arguments:  
  
    -   **\-Publisher**  
  
    -   **\-PublisherDB**  
  
    -   **\-PublisherSecurityMode** \= **1**  
  
    -   **\-Publication**  
  
    -   **\-Distributor**  
  
    -   **\-DistributorSecurityMode** \= **1**  
  
    -   **\-Subscriber**  
  
    -   **\-SubscriberSecurityMode** \= **1**  
  
    -   **\-SubscriberDB**  
  
    -   **\-SubscriptionType** \= **1**  
  
     If you are using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, you must also specify the following arguments:  
  
    -   **\-DistributorLogin**  
  
    -   **\-DistributorPassword**  
  
    -   **\-DistributorSecurityMode** \= **0**  
  
    -   **\-PublisherLogin**  
  
    -   **\-PublisherPassword**  
  
    -   **\-PublisherSecurityMode** \= **0**  
  
    -   **\-SubscriberLogin**  
  
    -   **\-SubscriberPassword**  
  
    -   **\-SubscriberSecurityMode** \= **0**  
  
###  <a name="TsqlExample"></a> Examples \(Replication Agents\)  
 The following example starts the Distribution Agent to synchronize a pull subscription. All connections are made using Windows Authentication.  
  
```  
 -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks  
SET SubscriptionDB=AdventureWorksReplica   
SET Publication=AdvWorksProductsTran  
  
-- Start the Distribution Agent.  
-- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\100\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 1;  
```  
  
 The following example starts the Merge Agent to synchronize a pull subscription. All connections are made using Windows Authentication.  
  
```  
-- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks  
SET SubscriptionDB=AdventureWorksReplica   
SET Publication=AdvWorksSalesOrdersMerge  
  
--Start the Merge Agent with concurrent upload and download processes.  
-- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\100\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
```  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can synchronize pull subscriptions programmatically by using Replication Management Objects \(RMO\) and managed code access to replication agent functionalities. The classes you use to synchronize a pull subscription depend on the type of publication to which the subscription belongs.  
  
> [!NOTE]  
>  If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously. However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process \(for example, to display a progress bar\), you should start the agent synchronously. For [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssExpressEd2005](../../Token\Other/ssExpressEd2005_md.md)] Subscribers, you must start the agent synchronously.  
  
#### To synchronize a pull subscription to a snapshot or transactional publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) class, and set the following properties:  
  
    -   The subscription database name for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName).  
  
    -   The name of the publication to which the subscription belongs for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName).  
  
    -   The name of the publication database for [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName).  
  
    -   The name of the Publisher for [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName).  
  
    -   The connection created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the remaining subscription properties. If this method returns **false**, verify that the subscription exists.  
  
4.  Start the Distribution Agent at the Subscriber in one of the following ways:  
  
    -   Call the [SynchronizeWithJob](assetId:///M:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob) method on the instance of [TransPullSubscription](assetId:///T:Microsoft.SqlServer.Replication.TransPullSubscription) from step 2. This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running. You cannot call this method for [!INCLUDE[ssExpressEd2005](../../Token\Other/ssExpressEd2005_md.md)] Subscribers or if the subscription was created with a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) \(the default\).  
  
    -   Get an instance of the [TransSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.TransSynchronizationAgent) class from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent) property, and call the [Synchronize](assetId:///M:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize) method. This method starts the agent synchronously, and control remains with the running agent job. During synchronous execution, you can handle the [Status](assetId:///E:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status) event while the agent is running.  
  
        > [!NOTE]  
        >  If you specified a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) \(the default\) when you created the pull subscription, you also need to specify [Distributor](assetId:///P:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor), [DistributorSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode), and optionally [DistributorLogin](assetId:///P:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin) and [DistributorPassword](assetId:///P:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword) because the agent job related metadata for the subscription is not available in [MSsubscription\_properties](../Topic/MSsubscription_properties%20\(Transact-SQL\).md).  
  
#### To synchronize a pull subscription to a merge publication  
  
1.  Create a connection to the Subscriber by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) class, and set the following properties:  
  
    -   The subscription database name for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName).  
  
    -   The name of the publication to which the subscription belongs for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationName).  
  
    -   The name of the published database for [PublicationDBName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName).  
  
    -   The name of the Publisher for [PublisherName](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.PublisherName).  
  
    -   The connection created in step 1 for [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext).  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the remaining subscription properties. If this method returns **false**, verify that the subscription exists.  
  
4.  Start the Merge Agent at the Subscriber in one of the following ways:  
  
    -   Call the [SynchronizeWithJob](assetId:///M:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob) method on the instance of [MergePullSubscription](assetId:///T:Microsoft.SqlServer.Replication.MergePullSubscription) from step 2. This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running. You cannot call this method for [!INCLUDE[ssExpressEd2005](../../Token\Other/ssExpressEd2005_md.md)] Subscribers or if the subscription was created with a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) \(the default\).  
  
    -   Obtain an instance of the [MergeSynchronizationAgent](assetId:///T:Microsoft.SqlServer.Replication.MergeSynchronizationAgent) class from the [SynchronizationAgent](assetId:///P:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent) property, and call the [Synchronize](assetId:///M:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize) method. This method starts the Merge Agent synchronously, and control remains with the running agent job. During synchronous execution, you can handle the [Status](assetId:///E:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status) event while the agent is running.  
  
        > [!NOTE]  
        >  If you specified a value of **false** for [CreateSyncAgentByDefault](assetId:///P:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault) \(the default\) when you created the pull subscription, you also need to specify [Distributor](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor), [DistributorSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode), [PublisherSecurityMode](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode), [HostName](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName), [SubscriptionType](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType), [ExchangeType](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType), and optionally [DistributorLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin), [DistributorPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword), [PublisherLogin](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin), and [PublisherPassword](assetId:///P:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword) because the agent job related metadata for the subscription is not available in [MSsubscription\_properties](../Topic/MSsubscription_properties%20\(Transact-SQL\).md).  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example synchronizes a pull subscription to a transactional publication, where the agent is started asynchronously using the agent job.  
  
```c#  
// Define server, publication, and database names.  
String subscriberName = subscriberInstance;  
String publisherName = publisherInstance;  
String publicationName = "AdvWorksProductTran";  
String publicationDbName = "AdventureWorks";  
String subscriptionDbName = "AdventureWorksReplica";  
  
// Create a connection to the Subscriber.  
ServerConnection conn = new ServerConnection(subscriberName);  
  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    conn.Connect();  
  
    // Define subscription properties.  
    subscription = new TransPullSubscription();  
    subscription.ConnectionContext = conn;  
    subscription.DatabaseName = subscriptionDbName;  
    subscription.PublisherName = publisherName;  
    subscription.PublicationDBName = publicationDbName;  
    subscription.PublicationName = publicationName;  
  
    // If the pull subscription and the job exists, start the agent job.  
    if (subscription.LoadProperties() && subscription.AgentJobId != null)  
    {  
        subscription.SynchronizeWithJob();  
    }  
    else  
    {  
        // Do something here if the subscription does not exist.  
        throw new ApplicationException(String.Format(  
            "A subscription to '{0}' does not exists on {1}",  
            publicationName, subscriberName));  
    }  
}  
catch (Exception ex)  
{  
    // Do appropriate error handling here.  
    throw new ApplicationException("The subscription could not be synchronized.", ex);  
}  
finally  
{  
    conn.Disconnect();  
}  
```  
  
```vb  
' Define server, publication, and database names.  
Dim subscriberName As String = subscriberInstance  
Dim publisherName As String = publisherInstance  
Dim publicationName As String = "AdvWorksProductTran"  
Dim publicationDbName As String = "AdventureWorks"  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
  
' Create a connection to the Subscriber.  
Dim conn As ServerConnection = New ServerConnection(subscriberName)  
  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    conn.Connect()  
  
    ' Define subscription properties.  
    subscription = New TransPullSubscription()  
    subscription.ConnectionContext = conn  
    subscription.DatabaseName = subscriptionDbName  
    subscription.PublisherName = publisherName  
    subscription.PublicationDBName = publicationDbName  
    subscription.PublicationName = publicationName  
  
    ' If the pull subscription and the job exists, start the agent job.  
    If subscription.LoadProperties() And Not subscription.AgentJobId Is Nothing Then  
        subscription.SynchronizeWithJob()  
    Else  
        ' Do something here if the subscription does not exist.  
        Throw New ApplicationException(String.Format( _  
         "A subscription to '{0}' does not exists on {1}", _  
         publicationName, subscriberName))  
    End If  
Catch ex As Exception  
    ' Do appropriate error handling here.  
    Throw New ApplicationException("The subscription could not be synchronized.", ex)  
Finally  
    conn.Disconnect()  
End Try  
```  
  
 This example synchronizes a pull subscription to a transactional publication, where the agent is started synchronously.  
  
```c#  
// Define the server, publication, and database names.  
string subscriberName = subscriberInstance;  
string publisherName = publisherInstance;  
string publicationName = "AdvWorksProductTran";  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
// Create a connection to the Subscriber.  
ServerConnection conn = new ServerConnection(subscriberName);  
  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    conn.Connect();  
  
    // Define the pull subscription.  
    subscription = new TransPullSubscription();  
    subscription.ConnectionContext = conn;  
    subscription.DatabaseName = subscriptionDbName;  
    subscription.PublisherName = publisherName;  
    subscription.PublicationDBName = publicationDbName;  
    subscription.PublicationName = publicationName;  
  
    // If the pull subscription exists, then start the synchronization.  
    if (subscription.LoadProperties())  
    {  
        // Check that we have enough metadata to start the agent.  
        if (subscription.PublisherSecurity != null)  
        {  
            // Synchronously start the Distribution Agent for the subscription.  
            subscription.SynchronizationAgent.Synchronize();  
        }  
        else  
        {  
            throw new ApplicationException("There is insufficent metadata to " +  
                "synchronize the subscription. Recreate the subscription with " +  
                "the agent job or supply the required agent properties at run time.");  
        }  
    }  
    else  
    {  
        // Do something here if the pull subscription does not exist.  
        throw new ApplicationException(String.Format(  
            "A subscription to '{0}' does not exist on {1}",  
            publicationName, subscriberName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement appropriate error handling here.  
    throw new ApplicationException("The subscription could not be " +  
        "synchronized. Verify that the subscription has " +  
        "been defined correctly.", ex);  
}  
finally  
{  
    conn.Disconnect();  
}  
```  
  
```vb  
' Define the server, publication, and database names.  
Dim subscriberName As String = subscriberInstance  
Dim publisherName As String = publisherInstance  
Dim publicationName As String = "AdvWorksProductTran"  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
' Create a connection to the Subscriber.  
Dim conn As ServerConnection = New ServerConnection(subscriberName)  
  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    conn.Connect()  
  
    ' Define the pull subscription.  
    subscription = New TransPullSubscription()  
    subscription.ConnectionContext = conn  
    subscription.DatabaseName = subscriptionDbName  
    subscription.PublisherName = publisherName  
    subscription.PublicationDBName = publicationDbName  
    subscription.PublicationName = publicationName  
  
    ' If the pull subscription exists, then start the synchronization.  
    If subscription.LoadProperties() Then  
        ' Check that we have enough metadata to start the agent.  
        If Not subscription.PublisherSecurity Is Nothing Then  
  
            ' Write agent output to a log file.  
            subscription.SynchronizationAgent.Output = "distagent.log"  
            subscription.SynchronizationAgent.OutputVerboseLevel = 2  
  
            ' Synchronously start the Distribution Agent for the subscription.  
            subscription.SynchronizationAgent.Synchronize()  
        Else  
            Throw New ApplicationException("There is insufficent metadata to " + _  
             "synchronize the subscription. Recreate the subscription with " + _  
             "the agent job or supply the required agent properties at run time.")  
        End If  
    Else  
        ' Do something here if the pull subscription does not exist.  
        Throw New ApplicationException(String.Format( _  
         "A subscription to '{0}' does not exist on {1}", _  
         publicationName, subscriberName))  
    End If  
Catch ex As Exception  
    ' Implement appropriate error handling here.  
    Throw New ApplicationException("The subscription could not be " + _  
     "synchronized. Verify that the subscription has " + _  
     "been defined correctly.", ex)  
Finally  
    conn.Disconnect()  
End Try  
```  
  
 This example synchronizes a pull subscription to a merge publication, where the agent is started asynchronously using the agent job.  
  
```c#  
// Define server, publication, and database names.  
String subscriberName = subscriberInstance;  
String publisherName = publisherInstance;  
String publicationName = "AdvWorksSalesOrdersMerge";  
String publicationDbName = "AdventureWorks";  
String subscriptionDbName = "AdventureWorksReplica";  
  
// Create a connection to the Subscriber.  
ServerConnection conn = new ServerConnection(subscriberName);  
  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    conn.Connect();  
  
    // Define subscription properties.  
    subscription = new MergePullSubscription();  
    subscription.ConnectionContext = conn;  
    subscription.DatabaseName = subscriptionDbName;  
    subscription.PublisherName = publisherName;  
    subscription.PublicationDBName = publicationDbName;  
    subscription.PublicationName = publicationName;  
  
    // If the pull subscription and the job exists, start the agent job.  
    if (subscription.LoadProperties() && subscription.AgentJobId != null)  
    {  
        subscription.SynchronizeWithJob();  
    }  
    else  
    {  
        // Do something here if the subscription does not exist.  
        throw new ApplicationException(String.Format(  
            "A subscription to '{0}' does not exists on {1}",  
            publicationName, subscriberName));  
    }  
}  
catch (Exception ex)  
{  
    // Do appropriate error handling here.  
    throw new ApplicationException("The subscription could not be synchronized.", ex);  
}  
finally  
{  
    conn.Disconnect();  
}  
```  
  
```vb  
' Define server, publication, and database names.  
Dim subscriberName As String = subscriberInstance  
Dim publisherName As String = publisherInstance  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publicationDbName As String = "AdventureWorks"  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
  
' Create a connection to the Subscriber.  
Dim conn As ServerConnection = New ServerConnection(subscriberName)  
  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    conn.Connect()  
  
    ' Define subscription properties.  
    subscription = New MergePullSubscription()  
    subscription.ConnectionContext = conn  
    subscription.DatabaseName = subscriptionDbName  
    subscription.PublisherName = publisherName  
    subscription.PublicationDBName = publicationDbName  
    subscription.PublicationName = publicationName  
  
    ' If the pull subscription and the job exists, start the agent job.  
    If subscription.LoadProperties() And Not subscription.AgentJobId Is Nothing Then  
        subscription.SynchronizeWithJob()  
    Else  
        ' Do something here if the subscription does not exist.  
        Throw New ApplicationException(String.Format( _  
         "A subscription to '{0}' does not exists on {1}", _  
         publicationName, subscriberName))  
    End If  
Catch ex As Exception  
    ' Do appropriate error handling here.  
    Throw New ApplicationException("The subscription could not be synchronized.", ex)  
Finally  
    conn.Disconnect()  
End Try  
```  
  
 This example synchronizes a pull subscription to a merge publication, where the agent is started synchronously.  
  
```c#  
// Define the server, publication, and database names.  
string subscriberName = subscriberInstance;  
string publisherName = publisherInstance;  
string publicationName = "AdvWorksSalesOrdersMerge";  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
// Create a connection to the Subscriber.  
ServerConnection conn = new ServerConnection(subscriberName);  
  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    conn.Connect();  
  
    // Define the pull subscription.  
    subscription = new MergePullSubscription();  
    subscription.ConnectionContext = conn;  
    subscription.DatabaseName = subscriptionDbName;  
    subscription.PublisherName = publisherName;  
    subscription.PublicationDBName = publicationDbName;  
    subscription.PublicationName = publicationName;  
  
    // If the pull subscription exists, then start the synchronization.  
    if (subscription.LoadProperties())  
    {  
        // Check that we have enough metadata to start the agent.  
        if (subscription.PublisherSecurity != null || subscription.DistributorSecurity != null)  
        {  
            // Synchronously start the Merge Agent for the subscription.  
            subscription.SynchronizationAgent.Synchronize();  
        }  
        else  
        {  
            throw new ApplicationException("There is insufficent metadata to " +  
                "synchronize the subscription. Recreate the subscription with " +  
                "the agent job or supply the required agent properties at run time.");  
        }  
    }  
    else  
    {  
        // Do something here if the pull subscription does not exist.  
        throw new ApplicationException(String.Format(  
            "A subscription to '{0}' does not exist on {1}",  
            publicationName, subscriberName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement appropriate error handling here.  
    throw new ApplicationException("The subscription could not be " +  
        "synchronized. Verify that the subscription has " +  
        "been defined correctly.", ex);  
}  
finally  
{  
    conn.Disconnect();  
}  
```  
  
```vb  
' Define the server, publication, and database names.  
Dim subscriberName As String = subscriberInstance  
Dim publisherName As String = publisherInstance  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
' Create a connection to the Subscriber.  
Dim conn As ServerConnection = New ServerConnection(subscriberName)  
  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    conn.Connect()  
  
    ' Define the pull subscription.  
    subscription = New MergePullSubscription()  
    subscription.ConnectionContext = conn  
    subscription.DatabaseName = subscriptionDbName  
    subscription.PublisherName = publisherName  
    subscription.PublicationDBName = publicationDbName  
    subscription.PublicationName = publicationName  
  
    ' If the pull subscription exists, then start the synchronization.  
    If subscription.LoadProperties() Then  
        ' Check that we have enough metadata to start the agent.  
        If Not subscription.PublisherSecurity Is Nothing Or subscription.DistributorSecurity Is Nothing Then  
  
            ' Output agent messages to the console.   
            subscription.SynchronizationAgent.OutputVerboseLevel = 1  
            subscription.SynchronizationAgent.Output = ""  
  
            ' Synchronously start the Merge Agent for the subscription.  
            subscription.SynchronizationAgent.Synchronize()  
        Else  
            Throw New ApplicationException("There is insufficent metadata to " + _  
             "synchronize the subscription. Recreate the subscription with " + _  
             "the agent job or supply the required agent properties at run time.")  
        End If  
    Else  
        ' Do something here if the pull subscription does not exist.  
        Throw New ApplicationException(String.Format( _  
         "A subscription to '{0}' does not exist on {1}", _  
         publicationName, subscriberName))  
    End If  
Catch ex As Exception  
    ' Implement appropriate error handling here.  
    Throw New ApplicationException("The subscription could not be " + _  
     "synchronized. Verify that the subscription has " + _  
     "been defined correctly.", ex)  
Finally  
    conn.Disconnect()  
End Try  
```  
  
 This example synchronizes a pull subscription to a merge publication using Web synchronization. The subscription was created without the agent job and related subscription metadata, so the agent must be started synchronously and additional subscription information is supplied.  
  
```c#  
// Define the server, publication, and database names.  
string subscriberName = subscriberInstance;  
string publisherName = publisherInstance;  
string distributorName = distributorInstance;  
string publicationName = "AdvWorksSalesOrdersMerge";  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
string webSyncUrl = "https://" + publisherInstance + "/SalesOrders/replisapi.dll";  
  
// Create a connection to the Subscriber.  
ServerConnection conn = new ServerConnection(subscriberName);  
  
MergePullSubscription subscription;  
MergeSynchronizationAgent agent;  
  
try  
{  
    // Connect to the Subscriber.  
    conn.Connect();  
  
    // Define the pull subscription.  
    subscription = new MergePullSubscription();  
    subscription.ConnectionContext = conn;  
    subscription.DatabaseName = subscriptionDbName;  
    subscription.PublisherName = publisherName;  
    subscription.PublicationDBName = publicationDbName;  
    subscription.PublicationName = publicationName;  
  
    // If the pull subscription exists, then start the synchronization.  
    if (subscription.LoadProperties())  
    {  
        // Get the agent for the subscription.  
        agent = subscription.SynchronizationAgent;  
  
        // Check that we have enough metadata to start the agent.  
        if (agent.PublisherSecurityMode == null)  
        {  
            // Set the required properties that could not be returned  
            // from the MSsubscription_properties table.   
            agent.PublisherSecurityMode = SecurityMode.Integrated;  
            agent.DistributorSecurityMode = SecurityMode.Integrated;  
            agent.Distributor = publisherName;  
            agent.HostName = hostname;  
  
            // Set optional Web synchronization properties.  
            agent.UseWebSynchronization = true;  
            agent.InternetUrl = webSyncUrl;  
            agent.InternetSecurityMode = SecurityMode.Standard;  
            agent.InternetLogin = winLogin;  
            agent.InternetPassword = winPassword;  
        }  
        // Enable agent output to the console.  
        agent.OutputVerboseLevel = 1;  
        agent.Output = "";  
  
        // Synchronously start the Merge Agent for the subscription.  
        agent.Synchronize();  
    }  
    else  
    {  
        // Do something here if the pull subscription does not exist.  
        throw new ApplicationException(String.Format(  
            "A subscription to '{0}' does not exist on {1}",  
            publicationName, subscriberName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement appropriate error handling here.  
    throw new ApplicationException("The subscription could not be " +  
        "synchronized. Verify that the subscription has " +  
        "been defined correctly.", ex);  
}  
finally  
{  
    conn.Disconnect();  
}  
```  
  
```vb  
' Define the server, publication, and database names.  
Dim subscriberName As String = subscriberInstance  
Dim publisherName As String = publisherInstance  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
Dim webSyncUrl As String = "https://" + publisherInstance + "/SalesOrders/replisapi.dll"  
  
' Create a connection to the Subscriber.  
Dim conn As ServerConnection = New ServerConnection(subscriberName)  
  
Dim subscription As MergePullSubscription  
Dim agent As MergeSynchronizationAgent  
  
Try  
    ' Connect to the Subscriber.  
    conn.Connect()  
  
    ' Define the pull subscription.  
    subscription = New MergePullSubscription()  
    subscription.ConnectionContext = conn  
    subscription.DatabaseName = subscriptionDbName  
    subscription.PublisherName = publisherName  
    subscription.PublicationDBName = publicationDbName  
    subscription.PublicationName = publicationName  
  
    ' If the pull subscription exists, then start the synchronization.  
    If subscription.LoadProperties() Then  
        ' Get the agent for the subscription.  
        agent = subscription.SynchronizationAgent  
  
        ' Check that we have enough metadata to start the agent.  
        If agent.PublisherSecurityMode = Nothing Then  
            ' Set the required properties that could not be returned  
            ' from the MSsubscription_properties table.   
            agent.PublisherSecurityMode = SecurityMode.Integrated  
            agent.Distributor = publisherInstance  
            agent.DistributorSecurityMode = SecurityMode.Integrated  
            agent.HostName = hostname  
  
            ' Set optional Web synchronization properties.  
            agent.UseWebSynchronization = True  
            agent.InternetUrl = webSyncUrl  
            agent.InternetSecurityMode = SecurityMode.Standard  
            agent.InternetLogin = winLogin  
            agent.InternetPassword = winPassword  
        End If  
  
        ' Enable agent logging to the console.  
        agent.OutputVerboseLevel = 1  
        agent.Output = ""  
  
        ' Synchronously start the Merge Agent for the subscription.  
        agent.Synchronize()  
    Else  
        ' Do something here if the pull subscription does not exist.  
        Throw New ApplicationException(String.Format( _  
         "A subscription to '{0}' does not exist on {1}", _  
         publicationName, subscriberName))  
    End If  
Catch ex As Exception  
    ' Implement appropriate error handling here.  
    Throw New ApplicationException("The subscription could not be " + _  
     "synchronized. Verify that the subscription has " + _  
     "been defined correctly.", ex)  
Finally  
    conn.Disconnect()  
End Try  
```  
  
## See Also  
 [Synchronize Data](../../Topics\TopicNameNotContainA/Synchronize-Data.md)   
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  