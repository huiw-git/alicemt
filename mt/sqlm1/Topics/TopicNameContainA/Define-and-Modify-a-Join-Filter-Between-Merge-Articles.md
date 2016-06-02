---
title: Define and Modify a Join Filter Between Merge Articles
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
---
# Define and Modify a Join Filter Between Merge Articles
  This topic describes how to define and modify a join filter between merge articles in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Merge replication supports join filters, which are typically used in conjunction with parameterized filters to extend table partitioning to other related table articles.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
-   **To define and modify a join filter between merge articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   To create a join filter, a publication must contain at least two related tables. A join filter extends a row filter; therefore you must define a row filter on one table before you can extend the filter with a join to another table. After one join filter is defined, you can extend this join filter with another join filter if the publication contains additional related tables.  
  
-   If you add, modify, or delete a join filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change. For more information about requirements for property changes, see [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the relationships between foreign keys and primary keys defined on the tables. For more information on generating a set of join filters automatically, see [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../Topic/Automatically%20Generate%20a%20Set%20of%20Join%20Filters%20Between%20Merge%20Articles%20\(SQL%20Server%20Management%20Studio\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Define, modify, and delete join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To define a join filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>**, select an existing row filter or join filter in the **Filtered Tables** pane.  
  
2.  Click **Add**, and then click **Add Join to Extend the Selected Filter**.  
  
3.  Create the join statement: select either **Use the builder to create the statement** or **Write the join the statement manually**.  
  
    -   If you select to use the builder, use the columns in the grid \(**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**\) to build a join statement.  
  
         Each column in the grid contains a drop\-down combo box, allowing you to select two columns and an operator \(**\=**, **\<\>**, **\<\=**, **\<**, **\>\=**, **\>**, and **like**\). The results are displayed in the **Preview** text area. If the join involves more than one pair of columns, select a conjunction \(AND or OR\) from the **Conjunction** column, and then enter two more columns and an operator.  
  
    -   If you select to write the statement manually, write the join statement in the **Join statement** text area. Use the **Filtered table columns** list box and the **Joined table columns** list box to drag and drop columns to the **Join statement** text area.  
  
    -   The complete join statement would appear like:  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         The JOIN clause should use two\-part naming; three\-part naming and four\-part naming are not supported.  
  
4.  Specify join options:  
  
    -   If the column on which you join in the filtered table \(the parent table\) is unique, select **Unique key**.  
  
        > [!CAUTION]  
        >  Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many. Only select this option if you have a constraint on the joining column in the child table that guarantees uniqueness. If the option is set incorrectly, non\-convergence of data can occur.  
  
    -   By default, merge replication processes changes on a row\-by\-row basis during synchronization. To have related changes in rows of both the filtered table and the joined table processed as a unit, select **Logical record** \([!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions only\). This option is available only if the article and publication requirements for using logical records are met. For more information see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md).  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
6.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To modify a join filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.  
  
2.  In the **Edit Join** dialog box, modify the filter.  
  
3.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
#### To delete a join filter  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties \- \<Publication\>**, select a filter in the **Filtered Tables** pane, and then click **Delete**. If the join filter you delete is itself extended by other joins, those joins will also be deleted.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 These procedures show a parameterized filter on a parent article with join filters between this article and related child articles. Join filters can be defined and modified programmatically using replication stored procedures.  
  
#### To define a join filter to extend an article filter to related articles in a merge publication  
  
1.  Define the filtering for the article being joined to, which is also known as the parent article.  
  
    -   For an article filtered using a parameterized row filter, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
    -   For an article filtered using a static row filter, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
2.  At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) to define one or more related articles, which are also known as child articles, for the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
3.  At the Publisher on the publication database, execute [sp_addmergefilter &#40;Transact-SQL&#41;](../Topic/sp_addmergefilter%20\(Transact-SQL\).md). Specify **@publication**, a unique name for this filter for **@filtername**, the name of the child article created in step 2 for **@article**, the name of the parent article being joined to for **@join\_articlename**, and one of the following values for **@join\_unique\_key**:  
  
    -   **0** \- indicates a many\-to\-one or many\-to\-many join between the parent and child articles.  
  
    -   **1** \- indicates a one\-to\-one or one\-to\-many join between the parent and child articles.  
  
     This defines a join filter between the two articles.  
  
    > [!CAUTION]  
    >  Only set **@join\_unique\_key** to **1** if you have a constraint on the joining column in the underlying table for the parent article that guarantees uniqueness. If **@join\_unique\_key** is set to **1** incorrectly, non\-convergence of data may occur.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example defines an article for a merge publication, where the `SalesOrderDetail` table article is filtered against the `SalesOrderHeader` table that is itself filtered using a static row filter. For more information, see [Define and Modify a Static Row Filter](../../Topics\TopicNameContainA/Define-and-Modify-a-Static-Row-Filter.md).  
  
 [!CODE [HowTo#sp_AddMergeArticle](../CodeSnippet/SQL15/replication/howto#sp_addmergearticle)]  
  
 This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the value of [HOST\_NAME](../Topic/HOST_NAME%20\(Transact-SQL\).md) in the **LoginID** column. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
 [!CODE [HowTo#sp_MergeDynamicPub1](../CodeSnippet/SQL15/replication/howto#sp_mergedynamicpub1)]  
  
## See Also  
 [Join Filters](../../Topics\TopicNameNotContainA/Join-Filters.md)   
 [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md)   
 [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Filter Published Data for Merge Replication](../../Topics\TopicNameNotContainA/Filter-Published-Data-for-Merge-Replication.md)   
 [How to: Define and Modify a Join Filter Between Merge Articles \(SQL Server Management Studio\)](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](../../Topics\TopicNameContainA/Define-a-Logical-Record-Relationship-Between-Merge-Table-Articles.md)   
 [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics\TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md)  
  
  