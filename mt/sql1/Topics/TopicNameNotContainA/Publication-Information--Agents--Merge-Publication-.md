---
title: "Publication Information, Agents (Merge Publication)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73ff590a-20da-4f10-b592-c60b7226d22b
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# Publication Information, Agents (Merge Publication)
The **Agents** tab displays summary information on the Snapshot Agent for the selected publication.  
  
## Options  
 For more detailed information and tasks related to the Snapshot Agent, right-click the row for the agent, and then click an option on the shortcut menu. To change the way that the grid displays data, right-click the grid, and then click one of the following options:  
  
-   **Sort**: Sort on one or more columns in the **Sort Columns** dialog box.  
  
-   **Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.  
  
-   **Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.  
  
-   **Clear Filter**: Clear any filter settings for the grid.  
  
 Filter settings are specific to each grid. Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.  
  
 **Status**  
 The status of the Snapshot Agent. The following list shows the possible status values:  
  
-   Error  
  
-   Retrying failed commands  
  
-   Not running  
  
-   Completed  
  
 **Agent**  
 The Snapshot Agent. This is the only agent associated with a merge publication. The Merge Agent is associated with subscriptions to this publication. For more information, see [View Information and Perform Tasks for the Agents Associated With a Subscription (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Subscription--Replication-Monitor-.md).  
  
 **Last Start Time**  
 The last time the agent started.  
  
 **Duration**  
 The amount of time the agent has run. The time represents elapsed time if the agent is currently running and total time if the agent has run previously.  
  
 **Last Action**  
 The last action performed during the most recent run of the agent.  
  
## See Also  
 [Start the Replication Monitor](../../Topics/TopicNameNotContainA/Start-the-Replication-Monitor.md)   
 [View Information and Perform Tasks for a Publication (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-a-Publication--Replication-Monitor-.md)   
 [View Information and Perform Tasks for the Agents Associated With a Publication (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Publication--Replication-Monitor-.md)   
 [Monitoring Replication](../../Topics/TopicNameNotContainA/Monitoring-Replication.md)