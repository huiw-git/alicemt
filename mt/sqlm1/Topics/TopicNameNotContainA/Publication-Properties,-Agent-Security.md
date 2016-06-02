---
title: Publication Properties, Agent Security
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
---
# Publication Properties, Agent Security
  The **Agent Security** page of the **Publication Properties** dialog box allows you to access the settings for the accounts under which the following agents run and make connections to the computers in a replication topology:  
  
-   The Snapshot Agent for all publications.  
  
-   The Log Reader Agent for all transactional publications. There is one Log Reader Agent for each database published for transactional replication. Changing the Log Reader Agent settings affects all transactional publications in a database.  
  
-   The Queue Reader Agent for transactional publications that allow queued updating subscriptions. There is one Queue Reader Agent for each distribution database. Changing the Queue Reader Agent settings affects all transactional publications with queued updating subscriptions that use the same distribution database. For more information about Queue Reader Agent security settings, see [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md).  
  
 For more information about security settings and the permissions required by each agent, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## Options  
 **Security settings** or **Create Agent**  
 If an agent job has been created, click **Security settings** to access a dialog box that allows you to change the security settings for an agent. If an agent job has not been created, click **Create Agent** to create one and specify security settings.  
  
## See Also  
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md)   
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Security and Protection &#40;Replication&#41;](../Topic/Security%20and%20Protection%20\(Replication\).md)  
  
  