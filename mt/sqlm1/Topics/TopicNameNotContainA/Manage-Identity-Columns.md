---
title: Manage Identity Columns
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
---
# Manage Identity Columns
  This topic describes how to manage identity columns in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. When Subscriber inserts are replicated back to the Publisher, identity columns must be managed to avoid assignment of the same identity value at both the Subscriber and Publisher. Replication can manage identity ranges automatically or you can choose to manually handle identity range management.  For information about the identity range management options provided by replication, see [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To manage identity columns, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   When publishing a table in more than one publication, you must specify the same identity range management options for both publications. For more information, see "Publishing Tables in More Than One Publication" in [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md).  
  
-   To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../../Topics\TopicNameNotContainA/Sequence-Numbers.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Specify an identity column management option on the **Properties** tab of the **Article Properties \-\<Article\>** dialog box of the New Publication Wizard. For more information about using this wizard, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md). In the New Publication Wizard:  
  
-   If you select **Merge publication** or **Transactional publication with updating subscriptions** on the **Publication Type** page, select automatic or manual identity range management \(automatic, the default, is recommended\). After the table is published, the property cannot be modified, but other related properties can be modified.  
  
-   If you select other publication types, identity range management should be set to manual.  
  
 Modify identity ranges and thresholds on the **Properties** tab of the **Article Properties \-\<Article\>**, which is available in the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify an identity column management option  
  
1.  If the Publisher is running a version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] prior to [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], on the **Publication Type** page of the New Publication Wizard, select **Merge publication** or **Transactional publication with updating subscriptions**.  
  
2.  On the **Articles** page, select a table with an identity column.  
  
3.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.  
  
4.  On the **Properties** tab of the **Article Properties \- \<Article\>** dialog box, in the **Identity Range Management** section, set the **Automatically manage identity ranges** property to **Automatic** or **Manual** \(for Publishers running [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or later\), or **True** or **False** \(for Publishers running a version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] prior to [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]\).  
  
5.  If you selected **Automatic** or **True** in step 4, enter values for the options in the following table. For more information on how these settings are used, see the "Assigning Identity Ranges" section of [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
    |Option|Value|Description|  
    |------------|-----------|-----------------|  
    |**Publisher range size**|Integer value for range size \(for example, 20000\).|See the "Assigning Identity Ranges" section of [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).|  
    |**Subscriber range size**|Integer value for range size \(for example, 10000\).|See the "Assigning Identity Ranges" section of [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).|  
    |**Range threshold percentage**|Integer value for percent threshold \(for example, 90 is equivalent to 90 percent\).|Percent of total identity values used at a node before a new identity range is assigned.<br /><br /> <br /><br /> Note: This value must be specified, but it is only used by: Subscribers using queued updating subscriptions; and Subscribers to merge publications running [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] or previous versions of other SQL Server editions. For more information, see the "Assigning Identity Ranges" section of [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).|  
    |**Next range starting value**|Integer value. Read\-only.|The value at which the next range will start. For example, if the current range is 5001\-6000, this value will be 6001.|  
    |**Maximum identity value**|Integer value. Read\-only.|The largest value for the identity column. Determined by the base data type of the column.|  
    |**Increment**|Integer value. Read\-only.|The amount by which the number in the identity column should increase or decrease for each insert: typically set to 1.|  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
#### To modify identity ranges and thresholds after a table is published  
  
1.  On the **Articles** page of the **Publication Properties \- \<Publication\>** dialog box, select a table with an identity column.  
  
2.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.  
  
3.  On the **Properties** tab of the **Article Properties \- \<Article\>** dialog box, in the **Identity Range Management** section, enter values for one or more of the following properties: **Publisher range size**, **Subscriber range size**, and **Range threshold percentage**.  
  
4.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
5.  Click **OK** on the **Publication Properties \- \<Publication\>** dialog box.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 You can use replication stored procedures to specify identity range management options when an article is created.  
  
#### To enable automatic identity range management when defining articles for a transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). If the source table being published has an identity column, specify a value of **auto** for **@identityrangemanagementoption**, the range of identity values assigned to the Publisher for **@pub\_identity\_range**, the range of identity values assigned to each Subscribers for **@identity\_range**, and the percent of total identity values used before a new identity range is assigned for **@threshold**. For more information about defining articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  Ensure that the data type of the identity column is large enough to support the total range of identities being assigned to all Subscribers.  
  
#### To disable automatic identity range management when defining articles for a transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify a value of **manual** for **@identityrangemanagementoption**. For more information about defining articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  Assign ranges to identity article columns at the Subscriber to avoid generating conflicts for updating Subscribers. For more information, see the section on assigning ranges for manual identity range management in the topic [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
#### To enable automatic identity range management when defining articles for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). If the source table being published has an identity column, specify a value of **auto** for **@identityrangemanagementoption**, the range of identity values assigned to a server subscription for **@pub\_identity\_range**, the range of identity values assigned to the Publisher and each client subscription for **@identity\_range**, and the percent of total identity values used before a new identity range is assigned for **@threshold**. For more information on when new identity ranges are assigned, see Assigning Identity Ranges in the topic [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md). For more information about defining articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  Ensure that the data type of the identity column is large enough to support the total range of identities being assigned to all Subscribers, particularly for Subscribers with server subscriptions.  
  
#### To disable automatic identity range management when defining articles for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify one of the following values for **@identityrangemanagementoption**:  
  
    -   **manual** \- Identity ranges must be assigned manually for updating Subscribers.  
  
    -   **none** \- Identity columns at the Publisher will not be defined as identity columns at the Subscriber.  
  
     For more information about defining articles, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
2.  Assign ranges to identity article columns at the Subscriber to avoid generating conflicts for updating Subscribers.  
  
#### To change automatic identity range management settings for an existing article in a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_helparticle](../Topic/sp_helparticle%20\(Transact-SQL\).md) and note the value of **identityrangemanagementoption** in the result set. If this value is **0**, automatic identity range management is not enabled.  
  
2.  If the value of **identityrangemanagementoption** in the result set is **1**, change the settings as follows:  
  
    -   To change the assigned identity ranges, execute [sp\_changearticle](../Topic/sp_changearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **identity\_range** or **pub\_identity\_range** for **@property** and the new range value for **@value**.  
  
    -   To change the threshold at which new ranges are assigned, execute [sp\_changearticle](../Topic/sp_changearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **threshold** for **@property** and the new threshold value for **@value**.  
  
#### To change automatic identity range management settings for an existing article in a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_helpmergearticle](../Topic/sp_helpmergearticle%20\(Transact-SQL\).md) and note the value of **identity\_support** in the result set. If this value is **0**, automatic identity range management is not enabled.  
  
2.  If the value of **identity\_support** in the result set is **1**, change the settings as follows:  
  
    -   To change the assigned identity ranges, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **identity\_range** or **pub\_identity\_range** for **@property** and the new range value for **@value**.  
  
    -   To change the threshold at which new ranges are assigned, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **threshold** for **@property** and the new threshold value for **@value**. For more information on when new identity ranges are assigned, see Assigning Identity Ranges in the topic [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
    -   To disable automatic identity range management, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md) at the Publisher on the publication database. Specify a value of **identityrangemanagementoption** for **@property** and either **manual** or **none** for **@value**.  
  
## See Also  
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md)  
  
  