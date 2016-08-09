---
title: "View Information and Perform Tasks for the Agents Associated With a Publication (Replication Monitor)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 40
manager: jhubbard
---
# View Information and Perform Tasks for the Agents Associated With a Publication (Replication Monitor)
Replication Monitor provides the **Agents** tab, which includes information about the agents associated with the selected publication. The Distribution Agent and Merge Agent are associated with subscriptions; for more information, see [View Information and Perform Tasks for the Agents Associated With a Subscription (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Subscription--Replication-Monitor-.md).  
  
 This tab displays information about the following agents:  
  
-   The Snapshot Agent, which is used by all publications.  
  
-   The Log Reader Agent, which is used by all transactional publications.  
  
-   The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.  
  
 To view more information about the options on this tab, click **Help** on the menu bar. For information about starting Replication Monitor, see [Start the Replication Monitor](../../Topics/TopicNameNotContainA/Start-the-Replication-Monitor.md).  
  
### To view information and perform tasks for the agents associated with a publication  
  
1.  Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.  
  
2.  Click the **Agents** tab to view information about agents. You can also access more detailed information and perform tasks on this tab:  
  
    -   To view detailed information about an agent (such as informational messages and any error messages), right-click the agent, and then click **View Details**.  
  
    -   To view detailed information about the job that runs the agent (such as the schedule, job step details, and so on), right-click the agent, and then click **Properties**.  
  
    -   To manage profiles for the agent, right-click the agent, and then click **Agent Profile**. For more information, see [Work with Replication Agent Profiles](../../Topics/TopicNameNotContainA/Work-with-Replication-Agent-Profiles.md).  
  
    -   To start an agent that is not running, right-click the agent, and then click **Start Agent**.  
  
    -   To stop an agent that is running, right-click the agent, and then click **Stop Agent**.  
  
## See Also  
 [Set Thresholds and Warnings in Replication Monitor](../../Topics/TopicNameNotContainA/Set-Thresholds-and-Warnings-in-Replication-Monitor.md)   
 [View Information and Perform Tasks for a Publication (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-a-Publication--Replication-Monitor-.md)   
 [Replication Agent Administration](../../Topics/TopicNameNotContainA/Replication-Agent-Administration.md)   
 [Monitoring Replication](../../Topics/TopicNameNotContainA/Monitoring-Replication.md)