---
title: Specify the Conflict Tracking and Resolution Level for Merge Articles
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
---
# Specify the Conflict Tracking and Resolution Level for Merge Articles
  This topic describes how to specify the conflict tracking and resolution level for merge articles in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 When a subscription to a merge publication is synchronized, replication checks for conflicts caused by changes to the same data made at both the Publisher and the Subscriber. You can specify whether conflicts are detected at the row\-level, where any change to the row is considered a conflict, or column\-level, where only changes to the same row and column are considered a conflict. Conflict resolution for articles is performed at the row\-level. For more information about conflict detection and resolution when logical records are used, see [Detecting and Resolving Conflicts in Logical Records](../../Topics\TopicNameNotContainA/Detecting-and-Resolving-Conflicts-in-Logical-Records.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   **To specify the conflict tracking and resolution level for merge articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If you modify the tracking level after subscriptions have been initialized, those subscriptions must be reinitialized. For more information about the effects of property changes, see [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
-   With row\- and column\-level tracking, conflict resolution is always performed at the row\-level: the winning row overwrites the losing row. Merge replication also allows you to specify that conflicts be tracked and resolved at the logical record level, but these options are not available from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For information about setting these options from replication stored procedures, see [Define a Logical Record Relationship Between Merge Table Articles](../../Topics\TopicNameContainA/Define-a-Logical-Record-Relationship-Between-Merge-Table-Articles.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Specify row\- or column\-level tracking for merge articles on the **Properties** tab of the **Article Properties** dialog box, which is available in the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify row\- or column\-level tracking  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties \- \<Publication\>** dialog box, select a table.  
  
2.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.  
  
3.  On the **Properties** tab of the **Article Properties \<Article\>** dialog box, select one of the following values for the **Tracking level** property: **Row\-level tracking** or **Column\-level tracking**.  
  
4.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To specify conflict tracking options for a new merge article  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md) and specify one of the following values for **@column\_tracking**:  
  
    -   **true** \- Use column\-level tracking for the article.  
  
    -   **false** \- Use row\-level tracking, which is the default.  
  
#### To change conflict tracking options for a merge article  
  
1.  To determine the conflict tracking options for a merge article, execute [sp\_helpmergearticle](../Topic/sp_helpmergearticle%20\(Transact-SQL\).md). Note the value of the **column\_tracking** option in the result set for the article. A value of **1** means that column\-level tracking is being used, and a value of **0** means that row\-level tracking is being used.  
  
2.  At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **column\_tracking** for **@property** and one of the following values for **@value**:  
  
    -   **true** \- Use column\-level tracking for the article.  
  
    -   **false** \- Use row\-level tracking, which is the default.  
  
     Specify a value of **1** for both **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**.  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)   
 [Detecting and Resolving Conflicts in Logical Records](../../Topics\TopicNameNotContainA/Detecting-and-Resolving-Conflicts-in-Logical-Records.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](../../Topics\TopicNameContainA/Define-a-Logical-Record-Relationship-Between-Merge-Table-Articles.md)   
 [Detect and Resolve Merge Replication Conflicts](../../Topics\TopicNameNotContainA/Detect-and-Resolve-Merge-Replication-Conflicts.md)  
  
  