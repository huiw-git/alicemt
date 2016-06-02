---
title: Specify Interactive Conflict Resolution for Merge Articles
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
---
# Specify Interactive Conflict Resolution for Merge Articles
  This topic describes how to specify interactive conflict resolution for merge articles in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on\-demand synchronization in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Synchronization Manager. After interactive resolution is enabled, resolve conflicts interactively during synchronization, using the Interactive Resolver. The Interactive Resolver is available through the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Synchronization Manager. For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../Topic/Synchronize%20a%20Subscription%20Using%20Windows%20Synchronization%20Manager%20\(Windows%20Synchronization%20Manager\).md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To specify interactive conflict resolution for merge articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   If a synchronization is performed outside of Windows Synchronization Manager \(as a scheduled synchronization or an on demand synchronization in SQL Server Management Studio or Replication Monitor\), conflicts are resolved automatically without user intervention, using the default conflict resolution specified for the article. For more information, see [Interactive Conflict Resolution](../../Topics\TopicNameNotContainA/Interactive-Conflict-Resolution.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To enable interactive conflict resolution for an article  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties \- \<Publication\>** dialog box, select a table. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
2.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.  
  
3.  On the **Article Properties \- \<Article\>** or **Article Properties \- \<ArticleType\>** page, click the **Resolver** tab.  
  
4.  Select **Allow Subscriber to resolve conflicts interactively during on\-demand synchronization**.  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
6.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To specify that a subscription should use interactive conflict resolution  
  
1.  In the **Subscription Properties \- \<Subscriber\>: \<SubscriptionDatabase\>** dialog box, specify a value of **True** for the **Resolve conflicts interactively** option. For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md) and [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md).  
  
2.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 You can programmatically specify that a Subscriber will use this graphical interface to resolve article conflicts when a pull subscription to a merge publication is created. Only conflicts in articles that support this option will be displayed in the Interactive Resolver.  
  
#### To create a merge pull subscription that uses the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp\_helpmergearticle](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md), specifying **@publication**. Note the value of **allow\_interactive\_resolver** for each article in the result set for which the Interactive Resolver will be used.  
  
    -   If this value is **1**, the Interactive Resolver will be used.  
  
    -   If this value is **0**, you must first enable the Interactive Resolver for each article. To do this, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md), specifying **@publication**, **@article**, a value of **allow\_interactive\_resolver** for **@property**, and a value of **true** for **@value**.  
  
2.  At the Subscriber on the subscription database, execute [sp\_addmergepullsubscription](../Topic/sp_addmergepullsubscription%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
3.  At the Subscriber on the subscription database, execute [sp\_addmergepullsubscription\_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md), specifying the following parameters:  
  
    -   **@publisher**, **@publisher\_db** \(the published database\), and **@publication**.  
  
    -   A value of **true** for **@enabled\_for\_syncmgr**.  
  
    -   A value of **true** for **@use\_interactive\_resolver**.  
  
    -   The security account information required by the Merge Agent. For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md).  
  
4.  At the Publisher on the publication database, execute [sp\_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md).  
  
#### To define an article that supports the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source\_object**, and a value of **true** for **@allow\_interactive\_resolver**. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
## See Also  
 [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../Topic/View%20and%20Resolve%20Data%20Conflicts%20for%20Merge%20Publications%20\(SQL%20Server%20Management%20Studio\).md)   
 [Interactive Conflict Resolution](../../Topics\TopicNameNotContainA/Interactive-Conflict-Resolution.md)  
  
  