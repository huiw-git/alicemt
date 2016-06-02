---
title: Start and Stop a Replication Agent (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
---
# Start and Stop a Replication Agent (SQL Server Management Studio)
  Start and stop agents from the **Jobs** folder and the **Replication** folder in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and from Replication Monitor. Start and stop the following agents and jobs:  
  
-   The Snapshot Agent, which is used by all publications.  
  
-   The Log Reader Agent, which is used by all transactional publications.  
  
-   The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.  
  
-   The Distribution Agent, which synchronizes subscriptions to transactional and snapshot publications.  
  
-   The Merge Agent, which synchronizes subscriptions to merge publications.  
  
-   Replication maintenance jobs.  
  
 For more information about starting the Merge Agent and the Distribution Agent, see [Synchronize a Push Subscription](../../Topics\TopicNameContainA/Synchronize-a-Push-Subscription.md) and [Synchronize a Pull Subscription](../../Topics\TopicNameContainA/Synchronize-a-Pull-Subscription.md). For more information about maintenance jobs, see [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../Topic/Run%20Replication%20Maintenance%20Jobs%20\(SQL%20Server%20Management%20Studio\).md).  
  
 For information about starting Replication Monitor, see [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md).  
  
### To start and stop a Snapshot Agent or Log Reader Agent from Management Studio  
  
1.  Connect to the Publisher in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node and the **Replication** folder.  
  
2.  Expand the **Local Publications** folder, and then right\-click a publication.  
  
3.  Click **View Snapshot Agent Status** or **View Log Reader Agent Status**.  
  
4.  Click **Start** or **Stop**.  
  
### To start and stop a Queue Reader Agent from Management Studio  
  
1.  Connect to the Distributor in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], and then expand the server node.  
  
2.  Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.  
  
3.  Right\-click the job for the agent, and then click **Start Job** or **Stop Job**. The name of the job for the Queue Reader Agent is in the form **\[\<Distributor\>\].\<integer\>**.  
  
### To start and stop a Snapshot Agent, Log Reader Agent, or Queue Reader Agent from Replication Monitor  
  
1.  Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.  
  
2.  Click the **Agents** tab.  
  
3.  Right\-click an agent, and then click **Start Agent** or **Stop Agent**.  
  
## See Also  
 [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md)   
 [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)  
  
  