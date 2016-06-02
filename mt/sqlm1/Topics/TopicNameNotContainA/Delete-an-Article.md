---
title: Delete an Article
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
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
---
# Delete an Article
  This topic describes how to delete an article in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or Replication Management Objects \(RMO\). For information about the conditions under which articles can be dropped and whether dropping an article requires a new snapshot or the reinitialization of subscriptions, see [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md).  
  
 **In This Topic**  
  
-   **To delete an article, using:**  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Articles can be deleted programmatically using replication stored procedures. The stored procedures that you use depend on the type of publication to which the article belongs.  
  
#### To delete an article from a snapshot or transactional publication  
  
1.  Execute [sp_droparticle &#40;Transact-SQL&#41;](../Topic/sp_droparticle%20\(Transact-SQL\).md) to delete an article, specified by **@article**, from a publication, specified by **@publication**. Specify a value of **1** for **@force\_invalidate\_snapshot**.  
  
2.  \(Optional\) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.  
  
#### To delete an article from a merge publication  
  
1.  Execute [sp_dropmergearticle &#40;Transact-SQL&#41;](../Topic/sp_dropmergearticle%20\(Transact-SQL\).md) to delete an article, specified by **@article**, from a publication, specified by **@publication**. If necessary, specify a value of **1** for **@force\_invalidate\_snapshot** and a value of **1** for **@force\_reinit\_subscription**.  
  
2.  \(Optional\) To remove the published object from the database entirely, execute the `DROP <objectname>` command at the Publisher on the publication database.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 The following example deletes an article from a transactional publication. Because this change invalidates the existing snapshot, a value of **1** is specified for the **@force\_invalidate\_snapshot** parameter.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'AdvWorksProductTran';   
SET @article = N'Product';   
  
-- Drop the transactional article.  
USE [AdventureWorks]  
EXEC sp_droparticle   
  @publication = @publication,   
  @article = @article,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
 The following example deletes two articles from a merge publication. Because these changes invalidate the existing snapshot, a value of **1** is specified for the **@force\_invalidate\_snapshot** parameter.  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
 You can delete articles programmatically by using Replication Management Objects \(RMO\). The RMO classes you use to delete an article depend on the type of publication to which the article belongs.  
  
#### To delete an article that belongs to a snapshot or transactional publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [TransArticle](assetId:///T:Microsoft.SqlServer.Replication.TransArticle) class.  
  
3.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name), [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName), and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName) properties.  
  
4.  Set the connection from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the article exists. If the value of this property is **false**, either the article properties in step 3 were defined incorrectly or the article does not exist.  
  
6.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Article.Remove) method.  
  
7.  Close all connections.  
  
#### To delete an article that belongs to a merge publication  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) class.  
  
3.  Set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name), [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName), and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Article.DatabaseName) properties.  
  
4.  Set the connection from step 1 for the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property.  
  
5.  Check the [IsExistingObject](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject) property to verify that the article exists. If the value of this property is **false**, either the article properties in step 3 were defined incorrectly or the article does not exist.  
  
6.  Call the [Remove](assetId:///M:Microsoft.SqlServer.Replication.Article.Remove) method.  
  
7.  Close all connections.  
  
## See Also  
 [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)  
  
  