---
title: Publish Data and Database Objects
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d986032c-3387-4de1-a435-3ec5e82185a2
---
# Publish Data and Database Objects
  When creating a publication, you choose the tables and other database objects that you want to publish. You can publish the following database objects using replication.  
  
|Database object|Snapshot replication and transactional replication|Merge replication|  
|---------------------|--------------------------------------------------------|-----------------------|  
|Tables|X|X|  
|Partitioned Tables|X|X|  
|Stored Procedures – Definition \([!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and CLR\)|X|X|  
|Stored Procedures – Execution \([!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and CLR\)|X|no|  
|Views|X|X|  
|Indexed Views|X|X|  
|Indexed Views as Tables|X|no|  
|User\-Defined Types \(CLR\)|X|X|  
|User\-Defined Functions \([!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and CLR\)|X|X|  
|Alias Data Types|X|X|  
|Full text indexes|X|X|  
|Schema Objects \(constraints, indexes, user DML triggers, extended properties, and collation\)|X|X|  
  
## Creating Publications  
 To create a publication, you supply the following information:  
  
-   The Distributor.  
  
-   The location of the snapshot files.  
  
-   The publication database.  
  
-   The type of publication to create \(snapshot, transactional, transactional with updatable subscriptions, or merge\).  
  
-   The data and database objects \(articles\) to include in the publication.  
  
-   Static row filters and column filters for all types of publications, and parameterized row filters and join filters for merge publications.  
  
-   The Snapshot Agent schedule.  
  
-   Accounts under which the following agents will run: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; the Queue Reader Agent for transactional publications that allow updating subscriptions.  
  
-   A name and description for the publication.  
  
 For information about how to work with publications, see the following topics:  
  
-   [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)  
  
-   [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md)  
  
-   [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)  
  
-   [View and Modify Article Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Article-Properties.md)  
  
-   [Delete a Publication](../../Topics\TopicNameContainA/Delete-a-Publication.md)  
  
-   [Delete an Article](../../Topics\TopicNameNotContainA/Delete-an-Article.md)  
  
> [!NOTE]  
>  Deleting an article or publication does not remove objects from the Subscriber.  
  
## Publishing Tables  
 The most commonly published object is a table. The following links provide additional information about areas related to publishing tables:  
  
-   [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md)  
  
-   [Article Options for Transactional Replication](../../Topics\TopicNameNotContainA/Article-Options-for-Transactional-Replication.md)  
  
-   [Article Options for Merge Replication](../../Topics\TopicNameNotContainA/Article-Options-for-Merge-Replication.md)  
  
-   [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md)  
  
 When publishing a table for replication, you can specify which schema objects should be copied to the Subscriber, such as declared referential integrity \(primary key constraints, reference constraints, unique constraints\), indexes, user DML triggers \(DDL triggers cannot be replicated\), extended properties, and collation. Extended properties are replicated only in the initial synchronization between the Publisher and the Subscriber. If you add or modify an extended property after the initial synchronization, the change is not replicated.  
  
 To specify schema options, see [Specify Schema Options](../../Topics\TopicNameNotContainA/Specify-Schema-Options.md) or [SchemaOption](assetId:///P:Microsoft.SqlServer.Replication.Article.SchemaOption).  
  
### Partitioned Tables and Indexes  
 Replication supports the publishing of partitioned tables and indexes. The level of support depends on the type of replication that is used, and the options that you specify for the publication and the articles associated with partitioned tables. For more information, see [Replicate Partitioned Tables and Indexes](../../Topics\TopicNameNotContainA/Replicate-Partitioned-Tables-and-Indexes.md).  
  
## Publishing Stored Procedures  
 All types of replication allow you to replicate stored procedure definitions: the CREATE PROCEDURE is copied to each Subscriber. In the case of common language runtime \(CLR\) stored procedures, the associated assembly is also copied. Changes to procedures are replicated to Subscribers; changes to associated assemblies are not.  
  
 In addition to replicating the definition of a stored procedure, transactional replication allows you to replicate the execution of stored procedures. This is useful in replicating the results of maintenance\-oriented stored procedures that affect large amounts of data. For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../../Topics\TopicNameNotContainA/Publishing-Stored-Procedure-Execution-in-Transactional-Replication.md).  
  
## Publishing Views  
 All types of replication allow you to replicate views. The view \(and its accompanying index, if it is an indexed view\) can be copied to the Subscriber, but the base table must also be replicated.  
  
 For indexed views, transactional replication also allows you to replicate the indexed view as a table rather than a view, eliminating the need to also replicate the base table. To do this, specify one of the "indexed view logbased" options for the *@type* parameter of [sp_addarticle &#40;Transact-SQL&#41;](../Topic/sp_addarticle%20\(Transact-SQL\).md). For more information about using **sp\_addarticle**, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
## Publishing User\-Defined Functions  
 The CREATE FUNCTION statements for CLR functions and [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] functions are copied to each Subscriber. In the case of CLR functions, the associated assembly is also copied. Changes to functions are replicated to Subscribers; changes to associated assemblies are not.  
  
## Publishing User\-Defined Types and Alias Data Types  
 Columns that use user\-defined types or alias data types are replicated to Subscribers like other columns. The CREATE TYPEstatement for each replicated type is executed at the Subscriber before the table is created. In the case of user\-defined types, the associated assembly is also copied to each Subscriber. Changes to user\-defined types and alias data types are not replicated to Subscribers.  
  
 If a type is defined in a database, but it is not referenced in any columns when a publication is created, the type is not copied to Subscribers. If you subsequently create a column of that type in the database and want to replicate it, you must first manually copy the type \(and the associated assembly for a user\-defined type\) to each Subscriber.  
  
## Publishing Full Text Indexes  
 The CREATE FULLTEXT INDEX statement is copied to each Subscriber, and the full text index is created at the Subscriber. Changes made to full text indexes using ALTER FULLTEXT INDEX are not replicated.  
  
## Making Schema Changes to Published Objects  
 Replication supports a wide range of schema changes to published objects. When you make any of the following schema changes on the appropriate published object at a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Publisher, that change is propagated by default to all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers:  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 For more information, see [Make Schema Changes on Publication Databases](../../Topics\TopicNameNotContainA/Make-Schema-Changes-on-Publication-Databases.md).  
  
## Considerations for Publishing  
 Keep the following issues in mind when publishing database objects:  
  
-   The database is accessible to users during the creation of the publication and the initial snapshot, but it is advisable to create publications during times of lower activity on the Publisher.  
  
-   A database cannot be renamed after a publication is created in it. To rename it, you must first remove replication from the database.  
  
-   If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects. For example, if you publish a view that depends on a table, you must publish the table also.  
  
    > [!NOTE]  
    >  If you add an article to a merge publication and an existing article depends on the new article, you must specify a processing order for both articles using the **@processing\_order** parameter of [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) and [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Consider the following scenario: you publish a table but you do not publish a function that the table references. If you do not publish the function, the table cannot be created at the Subscriber. When you add the function to the publication: specify a value of **1** for the **@processing\_order** parameter of **sp\_addmergearticle**; and specify a value of **2** for the **@processing\_order** parameter of **sp\_changemergearticle**, specifying the table name for the parameter **@article**. This processing order ensures that you create the function at the Subscriber before the table that depends on it. You can use different numbers for each article as long as the number for the function is lower than the number for the table.  
  
-   Publication names cannot include the following characters: % \* \[ \] | : " ? \\ \/ \< \>.  
  
### Limitations on Publishing Objects  
  
-   The maximum number of articles and columns that can be published differs by publication type. For more information, see the "Replication Objects" section of [Maximum Capacity Specifications for SQL Server](../../Topics\TopicNameNotContainA/Maximum-Capacity-Specifications-for-SQL-Server.md).  
  
-   Stored procedures, views, triggers, and user\-defined functions that are defined as WITH ENCRYPTION cannot be published as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication.  
  
-   XML schema collections can be replicated but changes are not replicated after the initial snapshot.  
  
-   Tables published for transactional replication must have a primary key. If a table is in a transactional replication publication, you cannot disable any indexes that are associated with primary key columns. These indexes are required by replication. To disable an index, you must first drop the table from the publication.  
  
-   Bound defaults created with [sp_bindefault &#40;Transact-SQL&#41;](../Topic/sp_bindefault%20\(Transact-SQL\).md) are not replicated \(bound defaults are deprecated in favor of defaults created with the DEFAULT keyword of ALTER TABLE or CREATE TABLE\).  
  
-   Functions containing the **NOEXPAND** hint on indexed views cannot be published in the same publication as the referenced tables and indexed views, due to the order in which the distribution agent delivers them. To work around this problem, place the table and indexed view creation in a first publication, and add functions containing the **NOEXPAND** hint on the indexed views to a second publication which you publish after the first publication completes. Or, create scripts for these functions and deliver the script by using the *@post\_snapshot\_script* parameter of **sp\_addpublication**.  
  
### Schemas and Object Ownership  
 Replication has the following default behavior in the New Publication Wizard with respect to schemas and object ownership:  
  
-   For articles in merge publications with a compatibility level of 90 or higher, snapshot publications, and transactional publications: by default, the object owner at the Subscriber is the same as the owner of the corresponding object at the Publisher. If the schemas that own objects do not exist at the Subscriber, they are created automatically.  
  
-   For articles in merge publications with a compatibility level lower than 90: by default, the owner is left blank and is specified as **dbo** during the creation of the object on the Subscriber.  
  
-   For articles in Oracle publications: by default, the owner is specified as **dbo**.  
  
-   For articles in publications that use character mode snapshots \(which are used for non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers and [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] Subscribers\): by default, the owner is left blank. The owner defaults to the owner associated with the account used by the Distribution Agent or Merge Agent to connect to the Subscriber.  
  
 The object owner can be changed through the **Article Properties \- \<***Article***\>** dialog box and through the following stored procedures: **sp\_addarticle**, **sp\_addmergearticle**, **sp\_changearticle**, and **sp\_changemergearticle**. For more information, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md), [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md), and [View and Modify Article Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Article-Properties.md).  
  
### Publishing Data to Subscribers Running Previous Versions of SQL Server  
  
-   If you are publishing to a Subscriber running a previous version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you are limited to the functionality of that version, both in terms of replication\-specific functionality and the functionality of the product as a whole.  
  
-   Merge publications use a compatibility level, which determines what features can be used in a publication and allows you to support Subscribers running previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### Publishing Tables in More Than One Publication  
 Replication supports publishing articles in multiple publications \(including republishing data\) with the following restrictions:  
  
-   If an article is published in a transactional publication and a merge publication, ensure that the *@published\_in\_tran\_pub* property is set to TRUE for the merge article. For more information about setting properties, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md) and [View and Modify Article Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Article-Properties.md).  
  
     You should also set the *@published\_in\_tran\_pub* property if an article is part of a transactional subscription and is included in a merge publication. If this is the case, be aware that by default transactional replication expects tables at the Subscriber to be treated as read\-only; if merge replication makes data changes to a table in a transactional subscription, non\-convergence of data can occur. To avoid this possibility, we recommend that any such table be specified as download\-only in the merge publication. This prevents a merge Subscriber from uploading data changes to the table. For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Download-Only-Articles.md).  
  
-   An article cannot be published in both a merge publication and a transactional publication with queued updating subscriptions.  
  
-   Articles included in transactional publications that support updating subscriptions cannot be republished.  
  
-   If an article is published in more than one transactional publication that supports queued updating subscriptions, the following properties must have the same value for the article across all publications:  
  
    |Property|Parameter in sp\_addarticle|  
    |--------------|---------------------------------|  
    |Identity range management|**@auto\_identity\_range** \(deprecated\) and **@identityrangemangementoption**|  
    |Publisher identity range|**@pub\_identity\_range**|  
    |Identity range|**@identity\_range**|  
    |Identity range threshold|**@threshold**|  
  
     For more information about these parameters, see [sp_addarticle &#40;Transact-SQL&#41;](../Topic/sp_addarticle%20\(Transact-SQL\).md).  
  
-   If an article is published in more than one merge publication, the following properties must have the same value for the article across all publications:  
  
    |Property|Parameter in sp\_addmergearticle|  
    |--------------|--------------------------------------|  
    |Column tracking|**@column\_tracking**|  
    |Schema options|**@schema\_option**|  
    |Column filtering|**@vertical\_partition**|  
    |Subscriber upload options|**@subscriber\_upload\_options**|  
    |Conditional delete tracking|**@delete\_tracking**|  
    |Error compensation|**@compensate\_for\_errors**|  
    |Identity range management|**@auto\_identity\_range** \(deprecated\) and **@identityrangemangementoption**|  
    |Publisher identity range|**@pub\_identity\_range**|  
    |Identity range|**@identity\_range**|  
    |Identity range threshold|**@threshold**|  
    |Partition options|**@partition\_options**|  
    |Blob column streaming|**@stream\_blob\_columns**|  
    |Filter type|**@filter\_type** \(parameter in **sp\_addmergefilter**\)|  
  
     For more information about these parameters, see [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) and [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md).  
  
-   Transactional replication and unfiltered merge replication support publishing a table in multiple publications and then subscribing within a single table in the subscription database \(commonly referred to as a roll up scenario\). Roll up is often used for aggregating subsets of data from multiple locations in one table at a central Subscriber. Filtered merge publications do not support the central Subscriber scenario. For merge replication, roll up is typically implemented through a single publication with parameterized row filters. For more information, see [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
## See Also  
 [Add Articles to and Drop Articles from Existing Publications](../../Topics\TopicNameNotContainA/Add-Articles-to-and-Drop-Articles-from-Existing-Publications.md)   
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Initialize a Subscription](../../Topics\TopicNameContainA/Initialize-a-Subscription.md)   
 [Scripting Replication](../../Topics\TopicNameNotContainA/Scripting-Replication.md)   
 [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  