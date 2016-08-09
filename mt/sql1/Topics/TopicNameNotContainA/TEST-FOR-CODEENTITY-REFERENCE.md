---
title: "TEST FOR CODEENTITY REFERENCE"
ms.custom: na
ms.date: 06/29/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e718f48f-1cdf-4517-8481-ccfcdd9bb920
caps.latest.revision: 3
---
# TEST FOR CODEENTITY REFERENCE
This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using replication programming or Replication Management Objects (RMO).  
  
 The [N:Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport?qualifyHint=False&autoUpgrade=True) namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process. Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.  
  
 The general process for implementing a business logic handler is:  
  
1.  Create the business logic hander assembly.  
  
2.  Register the assembly at the Distributor.  
  
3.  Deploy the assembly at the server on which the Merge Agent runs. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server.  
  
4.  Create an article that uses the business logic handler or modify an existing article to use the business logic handler.  
  
 The business logic handler you specify is executed for every row that is synchronized. Complex logic and calls to other applications or network services can impact performance. For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](../../Topics/TopicNameNotContainA/Execute-Business-Logic-During-Merge-Synchronization.md).  
  
 **In This Topic**  
  
-   **To implement a business logic handler for a merge article, using:**  
  
     [Replication Programming](#ReplProg)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="ReplProg"></a> Using Replication Programming  
  
#### To create and deploy a business logic handler  
  
1.  In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.  
  
2.  Add references to the project for the following namespaces.  
  
    |Assembly Reference|Location|  
    |------------------------|--------------|  
    |[N:Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport?qualifyHint=False&autoUpgrade=True)|[!INCLUDE[ssInstallPath](../../Topics/TopicNameContainA/tokens/ssInstallPath_md.md)]COM (default installation)|  
    |[System.Data](assetId:///N:System.Data?qualifyHint=False&autoUpgrade=True)|GAC (component of the .NET Framework)|  
    |[System.Data.Common](assetId:///N:System.Data.Common?qualifyHint=False&autoUpgrade=True)|GAC (component of the .NET Framework)|  
  
3.  Add a class that overrides the [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) class.  
  
4.  Implement the [P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates?qualifyHint=False&autoUpgrade=True) property to indicate the types of changes that are handled.  
  
5.  Override one or more of the following methods of the [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) class:  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)?qualifyHint=False&autoUpgrade=True) - invoked when a data change is committed during synchronization.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when DELETE statements are being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when INSERT statements are being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when UPDATE statements are being uploaded or downloaded.  
  
6.  Build the project to create the business logic handler assembly.  
  
7.  Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is [!INCLUDE[ssInstallPath](../../Topics/TopicNameContainA/tokens/ssInstallPath_md.md)]COM, or install it in the .NET global assembly cache (GAC). You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly. The assembly can be installed into the GAC using the Global Assembly Cache tool (**Gacutil.exe)** provided in the .NET Framework SDK.  
  
    > [!NOTE]  
    >  A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.  
  
#### To register a business logic handler  
  
1.  At the Publisher, execute [sp_enumcustomresolvers (Transact-SQL)](assetId:///81bd0d3a-48dc-42b1-b662-c630f61fc630) to verify that the assembly has not already been registered as a business logic handler.  
  
2.  At the Distributor, execute [sp_registercustomresolver (Transact-SQL)](assetId:///6d2b0472-0e1f-4005-833c-735d1940fe93), specifying a friendly name for the business logic handler for **@article_resolver**, a value of **true** for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) for **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**. When using Web synchronization, you must specify the location of assembly at the Web server.  
  
#### To use a business logic handler with a new table article  
  
1.  Execute [sp_addmergearticle (Transact-SQL)](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c) to define an article, specifying the friendly name of the business logic handler for **@article_resolver**. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
#### To use a business logic handler with an existing table article  
  
1.  Execute [sp_changemergearticle (Transact-SQL)](assetId:///0dc3da5c-4af6-45be-b5f0-074da182def2), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.  
  
###  <a name="TsqlExample"></a> Examples (Replication Programming)  
 This example shows a business logic handler that creates an audit log.  
  
 [!CODE [HowTo#rmo_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_businesslogiccode)]  
  
 [!CODE [HowTo#rmo_vb_BusinessLogicCode](../CodeSnippet/SQL15/replication/howto#rmo_vb_businesslogiccode)]  
  
 The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.  
  
 [!CODE [HowTo#sp_RegisterBLH_10](../CodeSnippet/SQL15/replication/howto#sp_registerblh_10)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects (RMO)  
  
#### To create a business logic handler  
  
1.  In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.  
  
2.  Add references to the project for the following namespaces.  
  
    |Assembly Reference|Location|  
    |------------------------|--------------|  
    |[N:Microsoft.SqlServer.Replication.BusinessLogicSupport](assetId:///N:Microsoft.SqlServer.Replication.BusinessLogicSupport?qualifyHint=False&autoUpgrade=True)|[!INCLUDE[ssInstallPath](../../Topics/TopicNameContainA/tokens/ssInstallPath_md.md)]COM (default installation)|  
    |[System.Data](assetId:///N:System.Data?qualifyHint=False&autoUpgrade=True)|GAC (component of the .NET Framework)|  
    |[System.Data.Common](assetId:///N:System.Data.Common?qualifyHint=False&autoUpgrade=True)|GAC (component of the .NET Framework)|  
  
3.  Add a class that overrides the [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) class.  
  
4.  Implement the [P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates?qualifyHint=False&autoUpgrade=True) property to indicate the types of changes that are handled.  
  
5.  Override one or more of the following methods of the [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) class:  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)?qualifyHint=False&autoUpgrade=True) - invoked when a data change is committed during synchronization.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when DELETE statements are being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when INSERT statements are being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.  
  
    -   [M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)](assetId:///M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)?qualifyHint=False&autoUpgrade=True) - invoked when UPDATE statements are being uploaded or downloaded.  
  
    > [!NOTE]  
    >  Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.  
  
6.  Build the project to create the business logic handler assembly.  
  
#### To register a business logic handler  
  
1.  Create a connection to the Distributor by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection?qualifyHint=False&autoUpgrade=True) class.  
  
2.  Create an instance of the [T:Microsoft.SqlServer.Replication.ReplicationServer](assetId:///T:Microsoft.SqlServer.Replication.ReplicationServer?qualifyHint=False&autoUpgrade=True) class. Pass the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection?qualifyHint=False&autoUpgrade=True) from step 1.  
  
3.  Call [M:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers](assetId:///M:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers?qualifyHint=False&autoUpgrade=True) and check the returned [ArrayList](assetId:///T:System.Collections.ArrayList?qualifyHint=False&autoUpgrade=True) object to ensure that the assembly has not already been registered as a business logic handler.  
  
4.  Create an instance of the [T:Microsoft.SqlServer.Replication.BusinessLogicHandler](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicHandler?qualifyHint=False&autoUpgrade=True) class. Specify the following properties:  
  
    -   [P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName?qualifyHint=False&autoUpgrade=True) - the name of the .NET assembly. If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name. You must include the full path with the assembly name when using a business logic handler with Web synchronization.  
  
    -   [P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName?qualifyHint=False&autoUpgrade=True) - the fully-qualified name of the class that overrides [T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule?qualifyHint=False&autoUpgrade=True) and implements the business logic handler.  
  
    -   [P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName?qualifyHint=False&autoUpgrade=True) - a friendly name you use when you access the business logic handler.  
  
    -   [P:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly?qualifyHint=False&autoUpgrade=True) - a value of **true**.  
  
#### To deploy a business logic handler  
  
1.  Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server. If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent. You may install the assembly in the GAC if there are multiple applications that use the same assembly.  
  
#### To use a business logic handler with a new table article  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection?qualifyHint=False&autoUpgrade=True) class.  
  
2.  Create an instance of the [T:Microsoft.SqlServer.Replication.MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle?qualifyHint=False&autoUpgrade=True) class. Set the following properties:  
  
    -   The name of the article for [P:Microsoft.SqlServer.Replication.Article.Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name?qualifyHint=False&autoUpgrade=True).  
  
    -   The name of the publication for [P:Microsoft.SqlServer.Replication.Article.PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName?qualifyHint=False&autoUpgrade=True).  
  
    -   The name of the publication database for [P:Microsoft.SqlServer.Replication.Article.DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName?qualifyHint=False&autoUpgrade=True).  
  
    -   The friendly name of the business logic handler ([P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName?qualifyHint=False&autoUpgrade=True)) for [P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver?qualifyHint=False&autoUpgrade=True).  
  
3.  Call the [M:Microsoft.SqlServer.Replication.Article.Create](assetId:///M:Microsoft.SqlServer.Replication.Article.Create?qualifyHint=False&autoUpgrade=True) method. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
#### To use a business logic handler with an existing table article  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection?qualifyHint=False&autoUpgrade=True) class.  
  
2.  Create an instance of the [T:Microsoft.SqlServer.Replication.MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle?qualifyHint=False&autoUpgrade=True) class.  
  
3.  Set the [P:Microsoft.SqlServer.Replication.Article.Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name?qualifyHint=False&autoUpgrade=True), [P:Microsoft.SqlServer.Replication.Article.PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName?qualifyHint=False&autoUpgrade=True), and [P:Microsoft.SqlServer.Replication.Article.DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName?qualifyHint=False&autoUpgrade=True) properties.  
  
4.  Set the connection from step 1 for the [P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext?qualifyHint=False&autoUpgrade=True) property.  
  
5.  Call the [M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties?qualifyHint=False&autoUpgrade=True) method to get the properties of the object. If this method returns **false**, either the article properties in step 3 were defined incorrectly or the article does not exist. For more information, see [View and Modify Article Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Article-Properties.md).  
  
6.  Set the friendly name of the business logic handler for [P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver?qualifyHint=False&autoUpgrade=True). This is the value of the [P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName](assetId:///P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName?qualifyHint=False&autoUpgrade=True) property specified when registering the business logic handler.  
  
###  <a name="PShellExample"></a> Examples (RMO)  
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
 [Implement a Custom Conflict Resolver for a Merge Article](../../Topics/TopicNameContainA/Implement-a-Custom-Conflict-Resolver-for-a-Merge-Article.md)   
 [Debug a Business Logic Handler (Replication Programming)](../../Topics/TopicNameContainA/Debug-a-Business-Logic-Handler--Replication-Programming-.md)   
 [Replication Security Best Practices](../../Topics/TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Programming with Replication Management Objects](assetId:///37476d50-fb47-49e3-9504-3b163ac381d8)