---
title: Specify Interactive Conflict Resolution for Merge Articles
H1: na
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
  This topic describes how to specify interactive conflict resolution for merge articles in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/includes/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)].  
  
 [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows Synchronization Manager. After interactive resolution is enabled, resolve conflicts interactively during synchronization, using the Interactive Resolver. The Interactive Resolver is available through the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] Windows Synchronization Manager. For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../../Topics/TopicNameContainA/Synchronize-a-Subscription-Using-Windows-Synchronization-Manager--Windows-Synchronization-Manager-.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To specify interactive conflict resolution for merge articles, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in SQL Server Management Studio or Replication Monitor), conflicts are resolved automatically without user intervention, using the default conflict resolution specified for the article. For more information, see [Interactive Conflict Resolution](../../Topics/TopicNameNotContainA/Interactive-Conflict-Resolution.md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To enable interactive conflict resolution for an article  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties - <Publication\>** dialog box, select a table. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics/TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
2.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.  
  
3.  On the **Article Properties - <Article\>** or **Article Properties - <ArticleType\>** page, click the **Resolver** tab.  
  
4.  Select **Allow Subscriber to resolve conflicts interactively during on-demand synchronization**.  
  
5.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/includes/clickOK_md.md)]  
  
6.  If you are in the **Publication Properties - <Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To specify that a subscription should use interactive conflict resolution  
  
1.  In the **Subscription Properties - <Subscriber\>: <SubscriptionDatabase\>** dialog box, specify a value of **True** for the **Resolve conflicts interactively** option. For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md) and [View and Modify Pull Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md).  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/includes/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 You can programmatically specify that a Subscriber will use this graphical interface to resolve article conflicts when a pull subscription to a merge publication is created. Only conflicts in articles that support this option will be displayed in the Interactive Resolver.  
  
#### To create a merge pull subscription that uses the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp_helpmergearticle](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md), specifying **@publication**. Note the value of **allow_interactive_resolver** for each article in the result set for which the Interactive Resolver will be used.  
  
    -   If this value is **1**, the Interactive Resolver will be used.  
  
    -   If this value is **0**, you must first enable the Interactive Resolver for each article. To do this, execute [sp_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md), specifying **@publication**, **@article**, a value of **allow_interactive_resolver** for **@property**, and a value of **true** for **@value**.  
  
2.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription](../Topic/sp_addmergepullsubscription%20\(Transact-SQL\).md). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
3.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription_agent](../Topic/sp_addmergepullsubscription_agent%20\(Transact-SQL\).md), specifying the following parameters:  
  
    -   **@publisher**, **@publisher_db** (the published database), and **@publication**.  
  
    -   A value of **true** for **@enabled_for_syncmgr**.  
  
    -   A value of **true** for **@use_interactive_resolver**.  
  
    -   The security account information required by the Merge Agent. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
4.  At the Publisher on the publication database, execute [sp_addmergesubscription](../Topic/sp_addmergesubscription%20\(Transact-SQL\).md).  
  
#### To define an article that supports the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source_object**, and a value of **true** for **@allow_interactive_resolver**. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
## See Also  
 [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/View-and-Resolve-Data-Conflicts-for-Merge-Publications--SQL-Server-Management-Studio-.md)   
 [Interactive Conflict Resolution](../../Topics/TopicNameNotContainA/Interactive-Conflict-Resolution.md)  
  
  