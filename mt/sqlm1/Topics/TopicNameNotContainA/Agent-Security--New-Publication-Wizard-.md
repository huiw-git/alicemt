---
title: Agent Security (New Publication Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
---
# Agent Security (New Publication Wizard)
  The **Agent Security** page allows you to specify the accounts under which the following agents run and make connections to the computers in a replication topology:  
  
-   The Snapshot Agent for all publications.  
  
-   The Log Reader Agent for all transactional publications.  
  
-   The Queue Reader Agent for transactional publications that allow updatable subscriptions. The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use. For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md).  
  
 For information about permissions required by agents and best practices for replication security, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
## Options  
 **Snapshot Agent**  
 Displayed for all publications. Click **Security Settings** to specify security settings in the **Snapshot Agent Security** dialog box.  
  
 Click **Help** on the **Snapshot Agent Security** dialog box for more information about the permissions required for accounts used by the Snapshot Agent.  
  
 **Log Reader Agent**  
 Displayed for all transactional publications. Click **Security Settings** to specify security settings in the **Log Reader Agent Security** dialog box.  
  
 Click **Help** on the **Log Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Log Reader Agent.  
  
> [!NOTE]  
>  There is one Log Reader Agent for each database that is published using transactional replication. If a transactional publication already exists in the database, the security settings are read\-only. You can change the settings in the **Publication Properties** dialog box, but changes affect all transactional publications in the database.  
  
 **Queue Reader Agent**  
 Displayed for transactional publications that allow updatable subscriptions. Click **Security Settings** to specify security settings in the **Queue Reader Agent Security** dialog box. A Queue Reader Agent job is created when this wizard completes; it does not depend on you creating any queued updating subscriptions. If you do not plan to create any queued updating subscriptions, you can disable the job. Right\-click the job \(named in the form: *\[\<Publisher\>\].\<integer\>*.\) in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent **Jobs** folder, and then click **Disable**.  
  
 Click **Help** on the **Queue Reader Agent Security** dialog box for more information about the permissions required for accounts used by the Queue Reader Agent.  
  
> [!NOTE]  
>  There is one Queue Reader Agent for each distribution database \(and all Publishers that it serves\). If a transactional publication that allows queued updating subscriptions already exists on any of the Publishers that use a given distribution database, the security settings are read\-only. You can change the account under which the Queue Reader Agent runs and makes connections in the **Distributor Properties** dialog box, but changes affect publications at all Publishers that use the distribution database.  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](../../Topics\TopicNameContainA/Create-an-Updatable-Subscription-to-a-Transactional-Publication.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)   
 [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)  
  
  