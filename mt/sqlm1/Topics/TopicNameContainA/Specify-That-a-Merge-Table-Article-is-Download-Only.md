---
title: Specify That a Merge Table Article is Download-Only
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
---
# Specify That a Merge Table Article is Download-Only
  This topic describes how to specify that a merge table article is download\-only in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Download\-only articles are designed for applications with data that is not updated at Subscribers. For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Download-Only-Articles.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   **To specify that a merge table article is download\-only, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If you specify that an article is download\-only after subscriptions have been initialized, all client subscriptions that received the article must be reinitialized. Server subscriptions do not have to be reinitialized. For more information on the effects of property changes, see [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Specify that an article is download\-only on the **Articles** page of the New Publication Wizard or the **Properties** tab of the **Article Properties \- \<Article\>** dialog box. This dialog box is available in the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify that an article is download\-only on the Articles page  
  
-   On the **Articles** page of the New Publication Wizard select a table, and then select the checkbox **Highlighted table is download\-only**.  
  
#### To specify that an article is download\-only on the Properties tab of the Article Properties \- \<Article\> dialog box  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties \- \<Publication\>** dialog box, select a table, and then click **Article Properties**.  
  
2.  Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.  
  
3.  In the **Destination Object** section of the **Properties** tab of the **Article Properties \- \<Article\>** dialog box, specify one of the following values for **Synchronization direction**:  
  
    -   **Download to Subscriber, prohibit Subscriber changes**  
  
    -   **Download to Subscriber, allow Subscriber changes**  
  
4.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To specify that a new merge table article is download\-only  
  
1.  Execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md), specifying a value of **1** or **2** for the parameter **@subscriber\_upload\_options**. The numbers correspond to the following behavior:  
  
    -   **0** \- No restrictions \(default\). Changes made at the Subscriber are uploaded to the Publisher.  
  
    -   **1** \- Changes are allowed at the Subscriber, but they are not uploaded to the Publisher.  
  
    -   **2** \- Changes are not allowed at the Subscriber.  
  
        > [!NOTE]  
        >  If the source table for an article is already published in another publication, the value of **@subscriber\_upload\_options** must be the same for both articles.  
  
#### To modify an existing merge table article to be download\-only  
  
1.  To determine if an article is download\-only, execute [sp\_helpmergearticle](../Topic/sp_helpmergearticle%20\(Transact-SQL\).md). Note the value of **upload\_options** for the article in the result set.  
  
2.  If the value returned in step 1 is **0**, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md), specifying a value of **subscriber\_upload\_options** for **@property**, a value of **1** for **@force\_invalidate\_snapshot** and **@force\_reinit\_subscription**, and a value of **1** or **2** for **@value**, which corresponds to the following behavior:  
  
    -   **1** \- Changes are allowed at the Subscriber, but they are not uploaded to the Publisher.  
  
    -   **2** \- Changes are not allowed at the Subscriber.  
  
        > [!NOTE]  
        >  If the source table for an article is already published in another publication, the download\-only behavior must be the same for both articles.  
  
## See Also  
 [Optimize Merge Replication Performance with Download-Only Articles](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Download-Only-Articles.md)   
 [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md)   
 [View and Modify Article Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Article-Properties.md)  
  
  