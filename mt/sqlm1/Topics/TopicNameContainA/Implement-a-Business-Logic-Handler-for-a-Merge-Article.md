---
title: Implement a Business Logic Handler for a Merge Article
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
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
---
# Implement a Business Logic Handler for a Merge Article
  This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using replication programming or Replication Management Objects \(RMO\).  
  
 The [Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport) namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process. Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.  
  
 The general process for implementing a business logic handler is:  
  
1.  Create the business logic hander assembly.  
  
2.  Register the assembly at the Distributor.  
  
3.  Deploy the assembly at the server on which the Merge Agent runs. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server.  
  
4.  Create an article that uses the business logic handler or modify an existing article to use the business logic handler.  
  
 The business logic handler you specify is executed for every row that is synchronized. Complex logic and calls to other applications or network services can impact performance. For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](../../Topics\TopicNameNotContainA/Execute-Business-Logic-During-Merge-Synchronization.md).  
  
 **In This Topic**  
  
-   **To implement a business logic handler for a merge article, using:**  
  
     [Replication Programming](#ReplProg)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="ReplProg"></a> Using Replication Programming  
  
#### To create and deploy a business logic handler  
  
1.  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.  
  
2.  Add references to the project for the following namespaces.  
  
    |Assembly Reference|Location|  
    |------------------------|--------------|  
    |[Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport)|[!INCLUDE[ssInstallPath](../../Token\Other/ssInstallPath_md.md)]COM \(default installation\)|  
    |[System.Data](assetId:///N:System.Data)|GAC \(component of the .NET Framework\)|  
    |[System.Data.Common](assetId:///N:System.Data.Common)|GAC \(component of the .NET Framework\)|  
  
3.  Add a class that overrides the [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) class.  
  
4.  Implement the [HandledChangeStates](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates) property to indicate the types of changes that are handled.  
  
5.  Override one or more of the following methods of the [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) class:  
  
    -   [CommitHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)) \- invoked when a data change is committed during synchronization.  
  
    -   [DeleteErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked when an error occurs when a DELETE statement is being uploaded or downloaded.  
  
    -   [DeleteHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)) \- invoked when DELETE statements are being uploaded or downloaded.  
  
    -   [InsertErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked when an error occurs when an INSERT statement is being uploaded or downloaded.  
  
    -   [InsertHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)) \- invoked when INSERT statements are being uploaded or downloaded.  
  
    -   [UpdateConflictsHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)) \- invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  
  
    -   [UpdateDeleteConflictHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)) \- invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  
  
    -   [UpdateErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.  
  
    -   [UpdateHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)) \- invoked when UPDATE statements are being uploaded or downloaded.  
  
6.  Build the project to create the business logic handler assembly.  
  
7.  Deploy the assembly in the directory that contains the Merge Agent executable file \(replmerg.exe\), which for a default installation is [!INCLUDE[ssInstallPath](../../Token\Other/ssInstallPath_md.md)]COM, or install it in the .NET global assembly cache \(GAC\). You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly. The assembly can be installed into the GAC using the Global Assembly Cache tool \(**Gacutil.exe\)** provided in the .NET Framework SDK.  
  
    > [!NOTE]  
    >  A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.  
  
#### To register a business logic handler  
  
1.  At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../Topic/sp_enumcustomresolvers%20\(Transact-SQL\).md) to verify that the assembly has not already been registered as a business logic handler.  
  
2.  At the Distributor, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](../Topic/sp_registercustomresolver%20\(Transact-SQL\).md), specifying a friendly name for the business logic handler for **@article\_resolver**, a value of **true** for **@is\_dotnet\_assembly**, the name of the assembly for **@dotnet\_assembly\_name**, and the fully\-qualified name of the class that overrides [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) for **@dotnet\_class\_name**.  
  
    > [!NOTE]  
    >  If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache \(GAC\), you need to specify the full path with the assembly name for **@dotnet\_assembly\_name**. When using Web synchronization, you must specify the location of assembly at the Web server.  
  
#### To use a business logic handler with a new table article  
  
1.  Execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to define an article, specifying the friendly name of the business logic handler for **@article\_resolver**. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
#### To use a business logic handler with an existing table article  
  
1.  Execute [sp_changemergearticle &#40;Transact-SQL&#41;](../Topic/sp_changemergearticle%20\(Transact-SQL\).md), specifying **@publication**, **@article**, a value of **article\_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.  
  
###  <a name="TsqlExample"></a> Examples \(Replication Programming\)  
 This example shows a business logic handler that creates an audit log.  
  
 [!CODE [HowTo#rmo_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_businesslogiccode)]  
  
 [!CODE [HowTo#rmo_vb_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_vb_businesslogiccode)]  
  
 The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.  
  
 [!CODE [HowTo#sp_RegisterBLH_10](../CodeSnippet/SQL15/replication/howto#sp_registerblh_10)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
  
#### To create a business logic handler  
  
1.  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.  
  
2.  Add references to the project for the following namespaces.  
  
    |Assembly Reference|Location|  
    |------------------------|--------------|  
    |[Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport)|[!INCLUDE[ssInstallPath](../../Token\Other/ssInstallPath_md.md)]COM \(default installation\)|  
    |[System.Data](assetId:///N:System.Data)|GAC \(component of the .NET Framework\)|  
    |[System.Data.Common](assetId:///N:System.Data.Common)|GAC \(component of the .NET Framework\)|  
  
3.  Add a class that overrides the [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) class.  
  
4.  Implement the [HandledChangeStates](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates) property to indicate the types of changes that are handled.  
  
5.  Override one or more of the following methods of the [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) class:  
  
    -   [CommitHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)) \- invoked when a data change is committed during synchronization.  
  
    -   [DeleteErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked if an error occurs while a DELETE statement is being uploaded or downloaded.  
  
    -   [DeleteHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)) \- invoked when DELETE statements are being uploaded or downloaded.  
  
    -   [InsertErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked if an error occurs when an INSERT statement is being uploaded or downloaded.  
  
    -   [InsertHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)) \- invoked when INSERT statements are being uploaded or downloaded.  
  
    -   [UpdateConflictsHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)) \- invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  
  
    -   [UpdateDeleteConflictHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)) \- invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  
  
    -   [UpdateErrorHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)) \- invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.  
  
    -   [UpdateHandler](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)) \- invoked when UPDATE statements are being uploaded or downloaded.  
  
    > [!NOTE]  
    >  Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.  
  
6.  Build the project to create the business logic handler assembly.  
  
#### To register a business logic handler  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) from step 1.  
  
3.  Call [EnumBusinessLogicHandlers](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers) and check the returned [ArrayList](assetId:///T:System.Collections.ArrayList) object to ensure that the assembly has not already been registered as a business logic handler.  
  
4.  Create an instance of the [BusinessLogicHandler](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicHandler) class. Specify the following properties:  
  
    -   [DotNetAssemblyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName) \- the name of the .NET assembly. If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name. You must include the full path with the assembly name when using a business logic handler with Web synchronization.  
  
    -   [DotNetClassName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName) \- the fully\-qualified name of the class that overrides [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) and implements the business logic handler.  
  
    -   [FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName) \- a friendly name you use when you access the business logic handler.  
  
    -   [IsDotNetAssembly](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly) \- a value of **true**.  
  
#### To deploy a business logic handler  
  
1.  Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server. If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent. You may install the assembly in the GAC if there are multiple applications that use the same assembly.  
  
#### To use a business logic handler with a new table article  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) class. Set the following properties:  
  
    -   The name of the article for [Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name).  
  
    -   The name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName).  
  
    -   The name of the publication database for [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName).  
  
    -   The friendly name of the business logic handler \([FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName)\) for [ArticleResolver](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver).  
  
3.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Article.Create) method. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
#### To use a business logic handler with an existing table article  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) class.  
  
3.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name), [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName), and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName) properties.  
  
4.  Set the connection from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the article properties in step 3 were defined incorrectly or the article does not exist. For more information, see [View and Modify Article Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Article-Properties.md).  
  
6.  Set the friendly name of the business logic handler for [ArticleResolver](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver). This is the value of the [FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName) property specified when registering the business logic handler.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.  
  
 [!CODE [HowTo#rmo_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_businesslogiccode)]  
  
 [!CODE [HowTo#rmo_vb_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_vb_businesslogiccode)]  
  
 This example registers a business logic handler at the Distributor.  
  
 [!CODE [HowTo#rmo_RegisterBLH_10](../CodeSnippet/SQL15/replication/howto#rmo_registerblh_10)]  
  
 [!CODE [HowTo#rmo_vb_RegisterBLH_10](../CodeSnippet/SQL15/replication/howto#rmo_vb_registerblh_10)]  
  
 This example changes an existing article to use the business logic handler.  
  
 [!CODE [HowTo#rmo_ChangeMergeArticle_BLH](../CodeSnippet/SQL15/replication/howto#rmo_changemergearticle_blh)]  
  
 [!CODE [HowTo#rmo_vb_ChangeMergeArticle_BLH](../CodeSnippet/SQL15/replication/howto#rmo_vb_changemergearticle_blh)]  
  
## See Also  
 [Implement a Custom Conflict Resolver for a Merge Article](../../Topics\TopicNameContainA/Implement-a-Custom-Conflict-Resolver-for-a-Merge-Article.md)   
 [Debug a Business Logic Handler &#40;Replication Programming&#41;](../Topic/Debug%20a%20Business%20Logic%20Handler%20\(Replication%20Programming\).md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Replication Management Objects Concepts](../Topic/Replication%20Management%20Objects%20Concepts.md)  
  
  