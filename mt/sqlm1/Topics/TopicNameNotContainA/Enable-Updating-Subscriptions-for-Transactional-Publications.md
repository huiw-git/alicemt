---
title: Enable Updating Subscriptions for Transactional Publications
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
---
# Enable Updating Subscriptions for Transactional Publications
  This topic describes how to enable updating subscriptions for transactional publications in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To enable updating subscriptions for transactional publications, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Enable updating subscriptions for transactional publications on the **Publication Type** page of the New Publication Wizard. For more information about using this wizard, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md). You cannot enable updating subscriptions after a publication is created.  
  
 To use updating subscriptions, you must also configure options in the New Subscription Wizard. For more information, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
#### To enable updating subscriptions  
  
1.  On the **Publication Type** page of the New Publication Wizard, select **Transactional publication with updatable subscriptions**.  
  
2.  On the **Agent Security** page, specify security settings for the Queue Reader Agent in addition to the Snapshot Agent and Log Reader Agent. For more information about the permissions required for the account under which the Queue Reader Agent runs, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
    > [!NOTE]  
    >  The Queue Reader Agent is configured even if you use only immediate updating subscriptions.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 When creating a transactional publication programmatically using replication stored procedures, you can enable either immediate or queued updating subscriptions.  
  
#### To create a publication that supports immediate updating subscriptions  
  
1.  If necessary, create a Log Reader Agent job for the publication database.  
  
    -   If a Log Reader Agent job already exists for the publication database, proceed to step 2.  
  
    -   If you are unsure whether a Log Reader Agent job exists for a published database, execute [sp_helplogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_helplogreader_agent%20\(Transact-SQL\).md) at the Publisher on the publication database. If the result set is empty, a Log Reader Agent job must be created.  
  
    -   At the publisher, execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md). Specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows credentials under which the agent runs for **@job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**.  
  
2.  Execute [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md), specifying a value of **true** for the parameter **@allow\_sync\_tran**.  
  
3.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 2 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
4.  Add articles to the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
5.  At the Subscriber, create an updating subscription to this publication. For more information, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
#### To create a publication that supports queued updating subscriptions  
  
1.  If necessary, create a Log Reader Agent job for the publication database.  
  
    -   If a Log Reader Agent job already exists for the publication database, proceed to step 2.  
  
    -   If you are unsure whether a Log Reader Agent job exists for a published database, execute [sp_helplogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_helplogreader_agent%20\(Transact-SQL\).md) at the Publisher on the publication database. If the result set is empty, then a Log Reader Agent job must be created.  
  
    -   At the publisher, execute [sp_addlogreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addlogreader_agent%20\(Transact-SQL\).md). Specify the Windows credentials under which the agent runs for **@job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**.  
  
2.  If necessary, create a Queue Reader Agent job for the Distributor.  
  
    -   If a Queue Reader Agent job already exists for the distribution database, proceed to step 3.  
  
    -   If you are unsure whether a Queue Reader Agent job exists for the distribution database, execute [sp_helpqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_helpqreader_agent%20\(Transact-SQL\).md) at the Distributor on the distribution database. If the result set is empty, then a Queue Reader Agent job must be created.  
  
    -   At the Distributor, execute [sp_addqreader_agent &#40;Transact-SQL&#41;](../Topic/sp_addqreader_agent%20\(Transact-SQL\).md). Specify the Windows credentials under which the agent runs for **@job\_name** and **@password**. These credentials are used when the Queue Reader Agent connects to the Publisher and Subscriber. For more information, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
3.  Execute [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md), specifying a value of **true** for the parameter **@allow\_queued\_tran** and a value of **pub wins**, **sub reinit**, or **sub wins** for **@conflict\_policy**.  
  
4.  At the Publisher, execute [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../Topic/sp_addpublication_snapshot%20\(Transact-SQL\).md). Specify the publication name used in step 3 for **@publication** and the Windows credentials under which the Snapshot Agent runs for **@snapshot\_job\_name** and **@password**. If the agent will use SQL Server Authentication when connecting to the Publisher, you must also specify a value of **0** for **@publisher\_security\_mode** and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login information for **@publisher\_login** and **@publisher\_password**. This creates a Snapshot Agent job for the publication.  
  
5.  Add articles to the publication. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
6.  At the Subscriber, create an updating subscription to this publication. For more information, see [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md).  
  
#### To change the conflict policy for a publication that allows queued updating subscriptions  
  
1.  At the Publisher on the publication database, execute [sp_changepublication &#40;Transact-SQL&#41;](../Topic/sp_changepublication%20\(Transact-SQL\).md). Specify a value of **conflict\_policy** for **@property** and the desired conflict policy mode of **pub wins**, **sub reinit**, or **sub wins** for **@value**.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 This example creates a publication that supported both immediate and queued updating pull subscriptions.  
  
 [!CODE [HowTo#sp_createtranupdatingpub](../CodeSnippet/SQL15/replication/howto#sp_createtranupdatingpub)]  
  
## See Also  
 [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../Topic/Set%20Queued%20Updating%20Conflict%20Resolution%20Options%20\(SQL%20Server%20Management%20Studio\).md)   
 [Publication Types for Transactional Replication](../../Topics\TopicNameNotContainA/Publication-Types-for-Transactional-Replication.md)   
 [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md)   
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md)   
 [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md)   
 [Use sqlcmd with Scripting Variables](../../Topics\TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md)  
  
  