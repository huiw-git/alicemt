---
title: Define a Logical Record Relationship Between Merge Table Articles
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
---
# Define a Logical Record Relationship Between Merge Table Articles
  This topic describes how to define a logical record relationship between merge table articles in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or Replication Management Objects \(RMO\).  
  
 Merge replication allows you to define a relationship between related rows in different tables. These rows can then be processed as a transactional unit during synchronization. A logical record can be defined between two articles whether or not they have a join filter relationship. For more information, see [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   **To define a logical record relationship between merge table articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [Replication Management Objects \(RMO\)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If you add, modify, or delete a logical record after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change. For more information about requirements for property changes, see [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Define logical records in the **Add Join** dialog box, which is available in the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
 Logical records can be defined in the **Add Join** dialog box only if they are applied to a join filter in a merge publication, and the publication follows the requirements for using precomputed partitions. To define logical records that are not applied to join filters and to set conflict detection and resolution at the logical record level, you must use stored procedures.  
  
#### To define a logical record relationship  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box, select a row filter in the **Filtered Tables** pane.  
  
     A logical record relationship is associated with a join filter, which extends a row filter. Therefore you must define a row filter before you can extend the filter with a join and apply a logical record relationship. After one join filter is defined, you can extend this join filter with another join filter. For more information about defining join filters, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
2.  Click **Add**, and then click **Add Join to Extend the Selected Filter**.  
  
3.  Define a join filter in the **Add Join** dialog box, and then select the check box **Logical Record**.  
  
4.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To delete a logical record relationship  
  
-   Delete only the logical record relationship or delete the logical record relationship and the join filter associated with it.  
  
     To delete only the logical record relationship:  
  
    1.  On the **Filter Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box, select the join filter associated with the logical record relationship in the **Filtered Tables** pane, and then click **Edit**.  
  
    2.  In the **Edit Join** dialog box, clear the check box **Logical Record**.  
  
    3.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
     To delete the logical record relationship and join filter associated with it:  
  
    -   On the **Filter Rows** page of the New Publication Wizard or **Publication Properties \- \<Publication\>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**. If the join filter you delete is itself extended by other joins, those joins will also be deleted.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 You can programmatically specify logical record relationships between articles using replication stored procedures.  
  
#### To define a logical record relationship without an associated join filter  
  
1.  If the publication contains any articles that are filtered, execute [sp\_helpmergepublication](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md), and note the value of **use\_partition\_groups** in the result set.  
  
    -   If the value is **1**, then precomputed partitions are already being used.  
  
    -   If the value is **0**, then execute [sp\_changemergepublication](../Topic/sp_changemergepublication%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **use\_partition\_groups** for **@property** and a value of **true** for **@value**.  
  
        > [!NOTE]  
        >  If the publication does not support precomputed partitions, then logical records cannot be used. For more information, see Requirements for Using Precomputed Partitions in the topic [Optimize Parameterized Filter Performance with Precomputed Partitions](../../Topics\TopicNameNotContainA/Optimize-Parameterized-Filter-Performance-with-Precomputed-Partitions.md).  
  
    -   If the value is NULL, then the Snapshot Agent needs to be run to generate the initial snapshot for the publication.  
  
2.  If the articles that will comprise the logical record do not exist, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify one of the following conflict detection and resolution options for the logical record:  
  
    -   To detect and resolve conflicts that occur within related rows in the logic record, specify a value of **true** for **@logical\_record\_level\_conflict\_detection** and **@logical\_record\_level\_conflict\_resolution**.  
  
    -   To use the standard row\- or column\-level conflict detection and resolution, specify a value of **false** for **@logical\_record\_level\_conflict\_detection** and **@logical\_record\_level\_conflict\_resolution**, which is the default.  
  
3.  Repeat step 2 for each article that will comprise the logical record. You must use the same conflict detection and resolution option for each article in the logical record. For more information, see [Detecting and Resolving Conflicts in Logical Records](../../Topics\TopicNameNotContainA/Detecting-and-Resolving-Conflicts-in-Logical-Records.md).  
  
4.  At the publisher on the publication database, execute [sp\_addmergefilter](../Topic/sp_addmergefilter%20\(Transact-SQL\).md). Specify **@publication**, the name of one article in the relationship for **@article**, the name of the second article for **@join\_articlename**, a name for the relationship for **@filtername**, a clause that defines the relationship between the two articles for **@join\_filterclause**, the type of join for **@join\_unique\_key** and one of the following values for **@filter\_type**:  
  
    -   **2** \- Defines a logical relationship.  
  
    -   **3** \- Defines a logical relationship with a join filter.  
  
    > [!NOTE]  
    >  If a join filter is not used, the direction of the relationship between the two articles is not important.  
  
5.  Repeat step 2 for each remaining logical record relationship in the publication.  
  
#### To change conflict detection and resolution for logical records  
  
1.  To detect and resolve conflicts that occur within related rows in the logical record:  
  
    -   At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **logical\_record\_level\_conflict\_detection** for **@property** and a value of **true** for **@value**. Specify a value of **1** for **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**.  
  
    -   At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **logical\_record\_level\_conflict\_resolution** for **@property** and a value of **true** for **@value**. Specify a value of **1** for **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**.  
  
2.  To use the standard row\-level or column\-level conflict detection and resolution:  
  
    -   At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **logical\_record\_level\_conflict\_detection** for **@property** and a value of **false** for **@value**. Specify a value of **1** for **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**.  
  
    -   At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **logical\_record\_level\_conflict\_resolution** for **@property** and a value of **false** for **@value**. Specify a value of **1** for **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**.  
  
#### To remove a logical record relationship  
  
1.  At the Publisher on the publication database, execute the following query to return information about all logical record relationships defined for the specified publication:  
  
     [!CODE [HowTo#sp_ReturnMergeLogicalRecords](../CodeSnippet/SQL15/replication/howto#sp_returnmergelogicalrecords)]  
  
     Note the name of the logical record relationship being removed in the **filtername** column in the result set.  
  
    > [!NOTE]  
    >  This query returns the same information as [sp\_helpmergefilter](../Topic/sp_helpmergefilter%20\(Transact-SQL\).md); however, this system stored procedure only returns information about logical record relationships that are also join filters.  
  
2.  At the Publisher on the publication database, execute [sp\_dropmergefilter](../Topic/sp_dropmergefilter%20\(Transact-SQL\).md). Specify **@publication**, the name of one of the articles in the relationship for **@article**, and the name of the relationship from step 1 for **@filtername**.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 This example enables precomputed partitions on an existing publication, and creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.  
  
 [!CODE [HowTo#sp_AddMergeLogicalRecord](../CodeSnippet/SQL15/replication/howto#sp_addmergelogicalrecord)]  
  
##  <a name="RMOProcedure"></a> Using Replication Management Objects \(RMO\)  
  
> [!NOTE]  
>  Merge replication allows you to specify that conflicts be tracked and resolved at the logical record level, but these options cannot be set using RMO.  
  
#### To define a logical record relationship without an associated join filter  
  
1.  Create a connection to the Publisher by using the [ServerConnection](assetId:///T:Microsoft.SqlServer.Management.Common.ServerConnection) class.  
  
2.  Create an instance of the [MergePublication](assetId:///T:Microsoft.SqlServer.Replication.MergePublication) class, set the [Name](assetId:///P:Microsoft.SqlServer.Replication.Publication.Name) and [DatabaseName](assetId:///P:Microsoft.SqlServer.Replication.Publication.DatabaseName) properties for the publication, and set the [ConnectionContext](assetId:///P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext) property to the connection created in step 1.  
  
3.  Call the [LoadProperties](assetId:///M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties) method to get the properties of the object. If this method returns **false**, either the publication properties in step 2 were defined incorrectly or the publication does not exist.  
  
4.  If the [PartitionGroupsOption](assetId:///P:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption) property is set to [False](assetId:///F:Microsoft.SqlServer.Replication.PartitionGroupsOption.False), set it to [True](assetId:///F:Microsoft.SqlServer.Replication.PartitionGroupsOption.True).  
  
5.  If the articles that are to comprise the logical record do not exist, create an instance of the [MergeArticle](assetId:///T:Microsoft.SqlServer.Replication.MergeArticle) class, and set the following properties:  
  
    -   The name of the article for [Name](assetId:///P:Microsoft.SqlServer.Replication.Article.Name).  
  
    -   The name of the publication for [PublicationName](assetId:///P:Microsoft.SqlServer.Replication.Article.PublicationName).  
  
    -   \(Optional\) If the article is horizontally filtered, specify the row filter clause for the [FilterClause](assetId:///P:Microsoft.SqlServer.Replication.MergeArticle.FilterClause) property. Use this property to specify a static or parameterized row filter. For more information, see [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
     For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
6.  Call the [Create](assetId:///M:Microsoft.SqlServer.Replication.Article.Create) method.  
  
7.  Repeat steps 5 and 6 for each article comprising the logical record.  
  
8.  Create an instance of the [MergeJoinFilter](assetId:///T:Microsoft.SqlServer.Replication.MergeJoinFilter) class to define the logical record relationship between articles. Then, set the following properties:  
  
    -   The name of the child article in the logical record relationship for the [ArticleName](assetId:///P:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName) property.  
  
    -   The name of the existing, parent article in the logical record relationship for the [JoinArticleName](assetId:///P:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName) property.  
  
    -   A name for the logical record relationship for the [FilterName](assetId:///P:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName) property.  
  
    -   The expression that defines the relationship for the [JoinFilterClause](assetId:///P:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause) property.  
  
    -   A value of [LogicalRecordLink](assetId:///F:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink) for the [FilterTypes](assetId:///P:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes) property. If the logical record relationship is also a join filter, specify a value of [JoinFilterAndLogicalRecordLink](assetId:///F:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink) for this property. For more information, see [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md).  
  
9. Call the [AddMergeJoinFilter](assetId:///M:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter(Microsoft.SqlServer.Replication.MergeJoinFilter)) method on the object that represents the child article in the relationship. Pass the [MergeJoinFilter](assetId:///T:Microsoft.SqlServer.Replication.MergeJoinFilter) object from step 8 to define the relationship.  
  
10. Repeat steps 8 and 9 for each remaining logical record relationship in the publication.  
  
###  <a name="PShellExample"></a> Example \(RMO\)  
 This example creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.  
  
 [!CODE [HowTo#rmo_CreateLogicalRecord](../CodeSnippet/SQL15/replication/howto#rmo_createlogicalrecord)]  
  
 [!CODE [HowTo#rmo_vb_CreateLogicalRecord](../CodeSnippet/SQL15/replication/howto#rmo_vb_createlogicalrecord)]  
  
## See Also  
 [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md)   
 [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md)   
 [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md)   
 [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md)   
 [Optimize Parameterized Filter Performance with Precomputed Partitions](../../Topics\TopicNameNotContainA/Optimize-Parameterized-Filter-Performance-with-Precomputed-Partitions.md)   
 [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md)  
  
  