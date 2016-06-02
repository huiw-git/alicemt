---
title: Define an Article
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
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
---
# Define an Article
  This topic describes how to define an article in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To define an article, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   Article names cannot include any of the following characters: % , \* , \[ , \] , | , : , " , ? , ' , \\ , \/ , \< , \>. If objects in the database include any of these characters and you want to replicate them, you must specify an article name that is different from the object name.  
  
##  <a name="Security"></a> Security  
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
 After a publication has been created, articles can be created programmatically using replication stored procedures. The stored procedures used to create an article will depend on the type of publication for which the article is being defined. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
#### To define an article for a Snapshot or Transactional Publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source\_object**, and any other optional parameters. Use **@source\_owner** to specify the schema ownership of the object, if not **dbo**. If the article is not a log\-based table article, specify the article type for **@type**; for more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](../Topic/Specify%20Article%20Types%20\(Replication%20Transact-SQL%20Programming\).md).  
  
2.  To horizontally filter rows in a table or view an article, use [sp\_articlefilter](../Topic/sp_articlefilter%20\(Transact-SQL\).md) to define the filter clause. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
3.  To vertically filter columns in a table or view an article, use [sp\_articlecolumn](../Topic/sp_articlecolumn%20\(Transact-SQL\).md). For more information, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
4.  Execute [sp\_articleview](../Topic/sp_articleview%20\(Transact-SQL\).md) if the article is filtered.  
  
5.  If the publication has existing subscriptions and [sp\_helppublication](../Topic/sp_helppublication%20\(Transact-SQL\).md) returns a value of **0** in the **immediate\_sync** column, you must call [sp\_addsubscription](../Topic/sp_addsubscription%20\(Transact-SQL\).md) to add the article to each existing subscription.  
  
6.  If the publication has existing pull subscriptions, execute [sp\_refreshsubscriptions](../Topic/sp_refreshsubscriptions%20\(Transact-SQL\).md) at the Publisher to create a new snapshot for existing pull subscriptions that contains just the new article.  
  
    > [!NOTE]  
    >  For subscriptions that are not initialized using a snapshot, you do not need to execute [sp\_refreshsubscriptions](../Topic/sp_refreshsubscriptions%20\(Transact-SQL\).md) as this procedure is executed by [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md).  
  
#### To define an article for a Merge Publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the name of the publication for **@publication**, a name for the article name for **@article**, and the object being published for **@source\_object**. To horizontally filter table rows, specify a value for **@subset\_filterclause**. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md) and [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md). If the article is not a table article, specify the article type for **@type**. For more information, see [Specify Article Types &#40;Replication Transact-SQL Programming&#41;](../Topic/Specify%20Article%20Types%20\(Replication%20Transact-SQL%20Programming\).md).  
  
2.  \(Optional\) At the Publisher on the publication database, execute [sp\_addmergefilter](../Topic/sp_addmergefilter%20\(Transact-SQL\).md) to define a join filter between two articles. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
3.  \(Optional\) At the Publisher on the publication database, execute [sp\_mergearticlecolumn](../Topic/sp_mergearticlecolumn%20\(Transact-SQL\).md) to filter table columns. For more information, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example defines an article based on the `Product` table for a transactional publication, where the article is filtered both horizontally and vertically.  
  
 [!CODE [HowTo#sp_AddTranArticle](../CodeSnippet/SQL15/replication/howto#sp_addtranarticle)]  
  
 This example defines articles for a merge publication, where the `SalesOrderHeader` article is statically filtered based on **SalesPersonID**, and the `SalesOrderDetail` article is join filtered based on `SalesOrderHeader`.  
  
 [!CODE [HowTo#sp_AddMergeArticle](../CodeSnippet/SQL15/replication/howto#sp_addmergearticle)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can define articles programmatically by using Replication Management Objects \(RMO\). The RMO classes that you use to define an article depend on the type of publication for which the article is defined.  
  
###  <a name="PShellExample"></a> Examples \(RMO\)  
 The following example adds an article with row and column filters to a transactional publication.  
  
 [!CODE [HowTo#rmo_CreateTranArticles](../CodeSnippet/SQL15/replication/howto#rmo_createtranarticles)]  
  
 [!CODE [HowTo#rmo_vb_CreateTranArticles](../CodeSnippet/SQL15/replication/howto#rmo_vb_createtranarticles)]  
  
 The following example adds three articles to a merge publication. The articles have column filters, and two join filters are used to propagate a parameterized row filter to the other articles.  
  
 [!CODE [HowTo#rmo_CreateMergeArticles](../CodeSnippet/SQL15/replication/howto#rmo_createmergearticles)]  
  
 [!CODE [HowTo#rmo_vb_CreateMergeArticles](../CodeSnippet/SQL15/replication/howto#rmo_vb_createmergearticles)]  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md)   
 [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)  
  
  