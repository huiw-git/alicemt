---
title: "Optimize Parameterized Row Filters"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
caps.handback.revision: 0
manager: jhubbard
---
# Optimize Parameterized Row Filters
This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To optimize parameterized row filters, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication. These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database. You can control how the data is shared among Subscribers by setting **partition options** when you create an article. For more information about these requirements, see [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
     With [!INCLUDE[ssEW](../../Topics/TopicNameContainA/tokens/ssEW_md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated. When set to false, the subscriber might have more rows than expected.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 The following settings can be used to optimize parameterized row filters:  
  
 **Partition Options**  
 Set this option on the **Properties** page of the **Article Properties - <Article\>** dialog box, or in the **Add Filter** dialog box. Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - <Publication\>** dialog box. The **Article Properties - <Article\>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.  
  
 **Precompute Partitions**  
 This option is set to **True** by default if the articles in your publication adhere to a set of requirements. For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../../Topics/TopicNameNotContainA/Optimize-Parameterized-Filter-Performance-with-Precomputed-Partitions.md). Modify this option on the **Subscription Options** page of the **Publication Properties - <Publication\>** dialog box.  
  
 **Optimize Synchronization**  
 This option should be set to **True** only if **Precompute Partitions** is set to **False**. Set this option on the **Subscription Options** page of the **Publication Properties - <Publication\>** dialog box.  
  
 For more information about using the New Publication Wizard and accessing the **Publication Properties - <Publication\>** dialog box, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To set Partition options in the Add Filter or Edit Filter dialog box  
  
1.  On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - <Publication\>** dialog box, click **Add**, and then click **Add Filter**.  
  
2.  Create a parameterized filter. For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics/TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md).  
  
3.  Select the option that matches how data will be shared among Subscribers:  
  
    -   **A row from this table will go to multiple subscriptions**  
  
    -   **A row from this table will go to only one subscription**  
  
     If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata. However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber. For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
4.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
5.  If you are in the **Publication Properties - <Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To set Partition Options in the Article Properties - <Article\> dialog box  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties - <Publication\>** dialog box, select a table, and then click **Article Properties**.  
  
2.  Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.  
  
3.  In the **Destination Object** section of the **Properties** tab of the **Article Properties - <Article\>** dialog box, specify one of the following values for **Partition Options**:  
  
    -   **Overlapping**  
  
    -   **Overlapping, disallow out-of-partition data changes**  
  
    -   **Nonoverlapping, single subscription**  
  
    -   **Nonoverlapping, shared between subscriptions**  
  
     For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
4.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
5.  If you are in the **Publication Properties - <Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To set Precompute Partitions  
  
1.  On the **Subscription Options** page of the **Publication Properties - <Publication\>** dialog box, select a value for the **Precompute Partitions** option. The property is read-only if:  
  
    -   The publication does not meet the requirements for precomputed partitions.  
  
    -   A snapshot has not yet been generated for the publication. In this case, the option displays a value of **Set automatically when a snapshot is created**.  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
#### To set Optimize Synchronization  
  
1.  On the **Subscription Options** page of the **Publication Properties - <Publication\>** dialog box, select a value of **True** for the **Optimize Synchronization** option.  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 For definitions of the filtering options for **@keep_partition_changes** and **@use_partition_groups**, see [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a).  
  
#### To specify merge filter optimizations when creating a new publication  
  
1.  At the Publisher on the publication database, execute [sp_addmergepublication](assetId:///28a629a1-7374-4614-9b04-279d290a942a). Specify **@publication** and a value of **true** for one the following parameters:  
  
    -   **@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions. For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../../Topics/TopicNameNotContainA/Optimize-Parameterized-Filter-Performance-with-Precomputed-Partitions.md).  
  
    -   **@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.  
  
2.  Add a snapshot job for the publication. For more information see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md).  
  
3.  At the Publisher on the publication database, execute [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c), specifying the following parameters:  
  
    -   **@publication** - the name of the publication from step 1.  
  
    -   **@article** - a name for the article  
  
    -   **@source_object** - the database object being published.  
  
    -   **@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.  
  
    -   **@partition_options** - the partition options for the filtered article.  
  
4.  Repeat step 3 for each article in the publication.  
  
5.  (Optional) At the Publisher on the publication database, execute [sp_addmergefilter](assetId:///4c118cb1-2008-44e2-a797-34b7dc34d6b1) to define a join filter between two articles. For more information, see [Define and Modify a Join Filter Between Merge Articles](../../Topics/TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
#### To view and modify merge filter behaviors for an existing publication  
  
1.  (Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](assetId:///dfe1e1e1-9a65-406a-aced-6385a078e135), specifying **@publication**. Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.  
  
2.  (Optional) At the Publisher on the publication database, execute [sp_changemergepublication](assetId:///81fe1994-7678-4852-980b-e02fedf1e796). Specify a value of **use_partition_groups** for **@property** and either **true** or **false** for **@value**.  
  
3.  (Optional) At the Publisher on the publication database, execute [sp_changemergepublication](assetId:///81fe1994-7678-4852-980b-e02fedf1e796). Specify a value of **keep_partition_changes** for **@property** and either **true** or **false** for **@value**.  
  
    > [!NOTE]  
    >  When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **@force_reinit_subscription**.  
  
4.  (Optional) At the Publisher on the publication database, execute [sp_changemergearticle](assetId:///0dc3da5c-4af6-45be-b5f0-074da182def2). Specify a value of **partition_options** for **@property** and the appropriate value for **@value**. See [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c) for definitions of these filtering options.  
  
5.  (Optional) Start the Snapshot Agent to regenerate the snapshot if necessary. For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](../../Topics/TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
## See Also  
 [Automatically Generate a Set of Join Filters Between Merge Articles (SQL Server Management Studio)](../../Topics/TopicNameContainA/Automatically-Generate-a-Set-of-Join-Filters-Between-Merge-Articles--SQL-Server-Management-Studio-.md)   
 [Define and Modify a Parameterized Row Filter for a Merge Article](../../Topics/TopicNameContainA/Define-and-Modify-a-Parameterized-Row-Filter-for-a-Merge-Article.md)   
 [Parameterized Row Filters](../../Topics/TopicNameNotContainA/Parameterized-Row-Filters.md)