---
title: Subscribers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
---
# Subscribers
  Specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers that will receive a subscription to the selected publication.  
  
## Options  
 **Subscribers**  
 Select the check box in the grid to enable the corresponding [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data source as a Subscriber to the publication chosen on the **Publication** page. If the Subscriber is not listed, click **Add Subscriber** or **Add SQL Server Subscriber**.  
  
 **Subscription database**  
 The information displayed in and actions available from this column depend on the type of Subscriber listed in the **Subscribers** column:  
  
-   For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers, select a subscription database from the **Subscription Database** list or create a new database by selecting the **New database** command from the same list.  
  
    > [!NOTE]  
    >  If you are enabling the Publisher as a Subscriber, the subscription database must be different from the publication database.  
  
-   For non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers, the subscription database is not displayed. Specify the database, along with other connection information, in the **Data source name** field of the **Add Non\-SQL Server** dialog box. This dialog box is available by clicking **Add Subscriber** and then clicking **Add Non\-SQL Server Subscriber**.  
  
 **Add Subscriber**  
 Add a server to the list of servers that can be enabled as Subscribers. This button is displayed when all of the following conditions are true:  
  
-   The publication you selected is a snapshot or transactional publication that does not support updating subscriptions.  
  
    > [!NOTE]  
    >  If the publication you are subscribing to has [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] subscriptions and the publication is not already enabled for non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Subscribers, you cannot add a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] subscription.  
  
-   The subscription is a push subscription.  
  
-   The Publisher of the selected publication is [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or later.  
  
 Clicking **Add Subscriber** shows a menu with two choices: **Add SQL Server Subscriber** and **Add Non\-SQL Server Subscriber**. Click **Add Non\-SQL Server Subscriber** to add an Oracle or IBM DB2 Subscriber.  
  
 **Add SQL Server Subscriber**  
 Add a server to the list of servers that can be enabled as Subscribers. This button is displayed when one or more of the following conditions is true:  
  
-   The publication you selected is a merge publication, or a snapshot or transactional publication that supports updating subscriptions.  
  
-   The subscription is a pull subscription.  
  
-   The Publisher of the selected publication is earlier than [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]. For earlier versions, the button is displayed only if one or more of the following conditions is true:  
  
    -   You are a member of the **sysadmin** fixed server role at the Publisher.  
  
    -   The Subscriber has been added on the **Subscribers** page of the **Publisher Properties** dialog box.  
  
    -   The publication allows anonymous subscriptions.  
  
## See Also  
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)   
 [Non-SQL Server Subscribers](../../Topics\TopicNameNotContainA/Non-SQL-Server-Subscribers.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  