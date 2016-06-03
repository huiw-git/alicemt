---
title: Define and Modify a Static Row Filter
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
---
# Define and Modify a Static Row Filter
  This topic describes how to define and modify a static row filter in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
-   **To define and modify a static row filter, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If you add, modify, or delete a static row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change. For more information about requirements for property changes, see [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
-   If the publication is enabled for peer\-to\-peer transactional replication, tables cannot be filtered.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   Because these filters are static, all subscribers will receive the same subset of the data. If you need to dynamically filter rows in a table article belonging to a merge publication so that each subscriber receives a different partition of the data, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md). Merge replication also enables you to filter related rows based on an existing row filter. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Define, modify, and delete static row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To define a static row filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box, the action you take depends on the type of publication:  
  
    -   For a snapshot or transactional publication, click **Add**.  
  
    -   For a merge publication, click **Add**, and then click **Add Filter**.  
  
2.  In the **Add Filter** dialog box, select a table to filter from the drop\-down list box.  
  
3.  Create a filter statement in the **Filter statement** text area. You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.  
  
    > [!NOTE]  
    >  The WHERE clause should use two\-part naming; three\-part naming and four\-part naming are not supported. If the publication is from an Oracle Publisher, the WHERE clause must be compliant with Oracle syntax.  
  
    -   The **Filter statement** text area includes the default text, which is in the form of:  
  
        ```tsql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax. The complete filter clause would appear like:  
  
        ```tsql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   A static row filter can include a user\-defined function. The complete filter clause for a static row filter with a user\-defined function would appear like:  
  
        ```tsql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
5.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To modify a static row filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Edit**.  
  
2.  In the **Edit Filter** dialog box, modify the filter.  
  
3.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
#### To delete a static row filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 When creating table articles, you can define a WHERE clause to filter rows out of an article. You can also change a row filter after it has been defined. Static row filters can be created and modified programmatically using replication stored procedures.  
  
#### To define a static row filter for a snapshot or transactional publication  
  
1.  Define the article to filter. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](../Topic/sp_articlefilter%20\(Transact-SQL\).md). Specify the name of the article for **@article**, the name of the publication for **@publication**, a name for the filter for **@filter\_name**, and the filtering clause for **@filter\_clause** \(not including `WHERE`\).  
  
3.  If a column filter must still be defined, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md). Otherwise, execute [sp_articleview &#40;Transact-SQL&#41;](../Topic/sp_articleview%20\(Transact-SQL\).md). Specify the publication name for **@publication**, the name of the filtered article for **@article**, and the filter clause specified in step 2 for **@filter\_clause**. This creates the synchronization objects for the filtered article.  
  
#### To modify a static row filter for a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](../Topic/sp_articlefilter%20\(Transact-SQL\).md). Specify the name of the article for **@article**, the name of the publication for **@publication**, a name for the new filter for **@filter\_name**, and the new filtering clause for **@filter\_clause** \(not including `WHERE`\). Because this change will invalidate data in existing subscriptions, specify a value of **1** for **@force\_reinit\_subscription**.  
  
2.  At the Publisher on the publication database, execute [sp_articleview &#40;Transact-SQL&#41;](../Topic/sp_articleview%20\(Transact-SQL\).md). Specify the publication name for **@publication**, the name of the filtered article for **@article**, and the filter clause specified in step 1 for **@filter\_clause**. This re\-creates the view that defines the filtered article.  
  
3.  Rerun the Snapshot Agent job for the publication to generate an updated snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
4.  Reinitialize subscriptions. For more information, see [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
#### To delete a static row filter for a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](../Topic/sp_articlefilter%20\(Transact-SQL\).md). Specify the name of the article for **@article**, the name of the publication for **@publication**, a value of NULL for **@filter\_name**, and a value of NULL for **@filter\_clause**. Because this change will invalidate data in existing subscriptions, specify a value of **1** for **@force\_reinit\_subscription**.  
  
2.  Rerun the Snapshot Agent job for the publication to generate an updated snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
3.  Reinitialize subscriptions. For more information, see [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
#### To define a static row filter for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the filtering clause for **@subset\_filterclause** \(not including `WHERE`\). For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  If a column filter must still be defined, see [Define and Modify a Column Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Column-Filter.md).  
  
#### To modify a static row filter for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify the publication name for **@publication**, the name of the filtered article for **@article**, a value of **subset\_filterclause** for **@property**, and the new filtering clause for **@value** \(not including `WHERE`\). Because this change will invalidate data in existing subscriptions, specify a value of 1 for **@force\_reinit\_subscription**.  
  
2.  Rerun the Snapshot Agent job for the publication to generate an updated snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
3.  Reinitialize subscriptions. For more information, see [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 In this transactional replication example, the article is filtered horizontally to remove all discontinued products.  
  
 [!CODE [HowTo#sp_AddTranArticle](../CodeSnippet/SQL15/replication/howto#sp_addtranarticle)]  
  
 In this merge replication example, the articles are filtered horizontally to return only rows that belong to the specified salesperson. A join filter is also used. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
 [!CODE [HowTo#sp_AddMergeArticle](../CodeSnippet/SQL15/replication/howto#sp_addmergearticle)]  
  
## See Also  
 [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md)   
 [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md)   
 [Filter Published Data for Merge Replication](../../Topics\TopicNameNotContainA/Filter-Published-Data-for-Merge-Replication.md)  
  
  