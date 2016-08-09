---
title: "Specify Interactive Conflict Resolution for Merge Articles"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Specify Interactive Conflict Resolution for Merge Articles
This topic describes how to specify interactive conflict resolution for merge articles in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows Synchronization Manager. After interactive resolution is enabled, resolve conflicts interactively during synchronization, using the Interactive Resolver. The Interactive Resolver is available through the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows Synchronization Manager. For more information, see [Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)](../../Topics/TopicNameContainA/Synchronize-a-Subscription-Using-Windows-Synchronization-Manager--Windows-Synchronization-Manager-.md).  
  
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
  
5.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
6.  If you are in the **Publication Properties - <Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
#### To specify that a subscription should use interactive conflict resolution  
  
1.  In the **Subscription Properties - <Subscriber\>: <SubscriptionDatabase\>** dialog box, specify a value of **True** for the **Resolve conflicts interactively** option. For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md) and [View and Modify Pull Subscription Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md).  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 You can programmatically specify that a Subscriber will use this graphical interface to resolve article conflicts when a pull subscription to a merge publication is created. Only conflicts in articles that support this option will be displayed in the Interactive Resolver.  
  
#### To create a merge pull subscription that uses the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp_helpmergearticle](assetId:///dfe1e1e1-9a65-406a-aced-6385a078e135), specifying **@publication**. Note the value of **allow_interactive_resolver** for each article in the result set for which the Interactive Resolver will be used.  
  
    -   If this value is **1**, the Interactive Resolver will be used.  
  
    -   If this value is **0**, you must first enable the Interactive Resolver for each article. To do this, execute [sp_changemergearticle](assetId:///0dc3da5c-4af6-45be-b5f0-074da182def2), specifying **@publication**, **@article**, a value of **allow_interactive_resolver** for **@property**, and a value of **true** for **@value**.  
  
2.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription](assetId:///d63909a0-8ea7-4734-9ce8-8204d936a3e4). For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
3.  At the Subscriber on the subscription database, execute [sp_addmergepullsubscription_agent](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb), specifying the following parameters:  
  
    -   **@publisher**, **@publisher_db** (the published database), and **@publication**.  
  
    -   A value of **true** for **@enabled_for_syncmgr**.  
  
    -   A value of **true** for **@use_interactive_resolver**.  
  
    -   The security account information required by the Merge Agent. For more information, see [Create a Pull Subscription](../../Topics/TopicNameContainA/Create-a-Pull-Subscription.md).  
  
4.  At the Publisher on the publication database, execute [sp_addmergesubscription](assetId:///a191d817-0132-49ff-93ca-76f13e609b38).  
  
#### To define an article that supports the Interactive Resolver  
  
1.  At the Publisher on the publication database, execute [sp_addmergearticle](assetId:///0df654ea-24e2-4c61-a75a-ecaa7a140a6c). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source_object**, and a value of **true** for **@allow_interactive_resolver**. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
## See Also  
 [View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-and-Resolve-Data-Conflicts-for-Merge-Publications--SQL-Server-Management-Studio-.md)   
 [Interactive Conflict Resolution](../../Topics/TopicNameNotContainA/Interactive-Conflict-Resolution.md)