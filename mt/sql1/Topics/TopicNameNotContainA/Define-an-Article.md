---
title: "Define an Article"
ms.custom: na
ms.date: 06/29/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
caps.handback.revision: 0
manager: jhubbard
---
# Define an Article
This topic describes how to define an article in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], or Replication Management Objects (RMO).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To define an article, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Article names cannot include any of the following characters: % , * , [ , ] , &#124; , : , " , ? , ' , \ , / , < , >. If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name.  
  
##  <a name="Security"></a> Security  
 When possible, prompt users to enter security credentials at runtime. If you must store credentials, use the [cryptographic services](http://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Create publications and define articles with the New Publication Wizard. After a publication is created, view and modify publication properties in the **Publication Properties - <Publication\>** dialog box. For information about creating a publication from an Oracle database, see [Create a Publication from an Oracle Database](../../Topics/TopicNameContainA/Create-a-Publication-from-an-Oracle-Database.md).  
  
#### To create a publication and define articles  
  
1.  Connect to the Publisher in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then right-click the **Local Publications** folder.  
  
3.  Click **New Publication**.  
  
4.  Follow the pages in the New Publication Wizard to:  
  
    -   Specify a Distributor if distribution has not been configured on the server. For more information about configuring distribution, see [Configure Publishing and Distribution](../../Topics/TopicNameNotContainA/Configure-Publishing-and-Distribution.md).  
  
         If you specify on the **Distributor** page that the Publisher server will act as its own Distributor (a local Distributor), and the server is not configured as a Distributor, the New Publication Wizard will configure the server. You will specify a default snapshot folder for the Distributor on the **Snapshot Folder** page. The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it. For more information about securing the folder appropriately, see [Secure the Snapshot Folder](../../Topics/TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
         If you specify that another server should act as the Distributor, you must enter a password on the **Administrative Password** page for connections made from the Publisher to the Distributor. This password must match the password specified when the Publisher was enabled at the remote Distributor.  
  
         For more information, see [Configure Distribution](../../Topics/TopicNameNotContainA/Configure-Distribution.md).  
  
    -   Choose a publication database.  
  
    -   Select a publication type. For more information, see [Types of Replication](../../Topics/TopicNameNotContainA/Types-of-Replication.md).  
  
    -   Specify data and database objects to publish; optionally filter columns from table articles, and set article properties.  
  
    -   Optionally filter rows from table articles. For more information, see [Filter Published Data](../../Topics/TopicNameNotContainA/Filter-Published-Data.md).  
  
    -   Set the Snapshot Agent schedule.  
  
    -   Specify the credentials under which the following replication agents run and make connections:  
  
         \- Snapshot Agent for all publications.  
  
         \- Log Reader Agent for all transactional publications.  
  
         \- Queue Reader Agent for transactional publications that allow updating subscriptions.  
  
         For more information, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics/TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
    -   Optionally script the publication. For more information, see [Scripting Replication](../../Topics/TopicNameNotContainA/Scripting-Replication.md).  
  
    -   Specify a name for the publication.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 After a publication has been created, articles can be created programmatically using replication stored procedures. The stored procedures used to create an article will depend on the type of publication for which the article is being defined. For more information, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
#### To define an article for a Snapshot or Transactional Publication  
  
1.  At the Publisher on the publication database, execute [sp_addarticle](assetId:///0483a157-e403-4fdb-b943-23c1b487bef0). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source_object**, and any other optional parameters. Use **@source_owner** to specify the schema ownership of the object, if not **dbo**. If the article is not a log-based table article, specify the article type for **@type**; for more information, see [Specify Article Types (Replication Transact-SQL Programming)](../../Topics/TopicNameNotContainA/Specify-Article-Types--Replication-Transact-SQL-Programming-.md).  
  
2.  To horizontally filter rows in a table or view an article, use [sp_articlefilter](assetId:///4c3fee32-a43f-4757-a029-30aef4696afb) to define the filter clause. For more information, see [Define and Modify a Static Row Filter](../../Topics/TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
3.  To vertically filter columns in a table or view an article, use [sp_articlecolumn](assetId:///8abaa8c1-d99e-4788-970f-c4752246c577). For more information, see [Define and Modify a Column Filter](../../Topics/TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
4.  Execute [sp_articleview](assetId:///a3d63fd6-f360-4a2f-8a82-a0dc15f650b3) if the article is filtered.  
  
5.  If the publication has existing subscriptions and [sp_helppublication](assetId:///e801c3f0-dcbd-4b4a-b254-949a05f63518) returns a value of **0** in the **immediate_sync** column, you must call [sp_addsubscription](assetId:///61ddf287-1fa0-4c1a-8657-ced50cebf0e0) to add the article to each existing subscription.  
  
6.  If the publication has existing pull subscriptions, execute [sp_refreshsubscriptions](assetId:///6cb9b1ce-1ce7-43ab-9451-201f79ed1ffa) at the Publisher to create a new snapshot for existing pull subscriptions that contains just the new article.  
  
    > [!NOTE]  
    >  For subscriptions that are not initialized using a snapshot, you do not need to execute [sp_refreshsubscriptions](assetId:///6cb9b1ce-1ce7-43ab-9451-201f79ed1ffa) as this procedure is executed by [sp_addarticle](assetId:///0483a157-e403-4fdb-b943-23c1b487bef0).  
  
#### To define an article for a Merge Publication  
  
1.  At the Publisher on the publication database, execute [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c). Specify the name of the publication for **@publication**, a name for the article name for **@article**, and the object being published for **@source_object**. To horizontally filter table rows, specify a value for **@subset_filterclause**. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics/TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md) and [Define and Modify a Static Row Filter](../../Topics/TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md). If the article is not a table article, specify the article type for **@type**. For more information, see [Specify Article Types (Replication Transact-SQL Programming)](../../Topics/TopicNameNotContainA/Specify-Article-Types--Replication-Transact-SQL-Programming-.md).  
  
2.  (Optional) At the Publisher on the publication database, execute [sp_addmergefilter](assetId:///4c118cb1-2008-44e2-a797-34b7dc34d6b1) to define a join filter between two articles. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics/TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
3.  (Optional) At the Publisher on the publication database, execute [sp_mergearticlecolumn](assetId:///b4f2b888-e094-4759-a472-d893638995eb) to filter table columns. For more information, see [Define and Modify a Column Filter](../../Topics/TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
###  <a name="TsqlExample"></a> Examples (Transact-SQL)  
 This example defines an article based on the `Product` table for a transactional publication, where the article is filtered both horizontally and vertically.  
  
 [!CODE [HowTo#sp_AddTranArticle](../CodeSnippet/SQL15/replication/howto#sp_addtranarticle)]  
  
 This example defines articles for a merge publication, where the `SalesOrderHeader` article is statically filtered based on **SalesPersonID**, and the `SalesOrderDetail` article is join filtered based on `SalesOrderHeader`.  
  
 [!CODE [HowTo#sp_AddMergeArticle](../CodeSnippet/SQL15/replication/howto#sp_addmergearticle)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects (RMO)  
 You can define articles programmatically by using Replication Management Objects (RMO). The RMO classes that you use to define an article depend on the type of publication for which the article is defined.  
  
###  <a name="PShellExample"></a> Examples (RMO)  
 The following example adds an article with row and column filters to a transactional publication.  
  
 [!CODE [HowTo#rmo_CreateTranArticles](../CodeSnippet/SQL15/replication/howto#rmo_createtranarticles)]  
  
 [!CODE [HowTo#rmo_vb_CreateTranArticles](../CodeSnippet/SQL15/replication/howto#rmo_vb_createtranarticles)]  
  
 The following example adds three articles to a merge publication. The articles have column filters, and two join filters are used to propagate a parameterized row filter to the other articles.  
  
 [!CODE [HowTo#rmo_CreateMergeArticles](../CodeSnippet/SQL15/replication/howto#rmo_createmergearticles)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergeArticles](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergearticles)]  
  
## See Also  
 [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md)   
 [Programming Replication Using System Stored Procedures](assetId:///816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a)   
 [Add Articles to and Drop Articles from Existing Publications](../../Topics/TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md)   
 [Filter Published Data](../../Topics/TopicNameNotContainA/Filter-Published-Data.md)   
 [Publish Data and Database Objects](../../Topics/TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Programming with Replication Management Objects](assetId:///816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a)