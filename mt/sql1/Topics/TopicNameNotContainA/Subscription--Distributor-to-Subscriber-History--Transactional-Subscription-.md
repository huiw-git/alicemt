---
title: "Subscription, Distributor to Subscriber History (Transactional Subscription)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
caps.latest.revision: 21
manager: jhubbard
---
# Subscription, Distributor to Subscriber History (Transactional Subscription)
The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.  
  
## Options  
 Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**. Detailed information on this session is displayed in the grid labeled **Actions in the selected session**. If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.  
  
 **View**  
 Select which Distribution Agent sessions to view. The Distribution Agent typically runs continuously, therefore there might be only one session to view.  
  
 **Status**  
 The status of the Distribution Agent. The following list shows the possible status values:  
  
-   Error  
  
-   Completed  
  
-   Retrying  
  
-   Running  
  
 **Start Time**  
 The start time of the session.  
  
 **End Time**  
 The end time of the session. If the agent has not stopped, this field is empty.  
  
 **Duration**  
 The amount of time the Distribution Agent has run in this session. The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.  
  
 **Error Message**  
 If a session ended in an error, this field displays the last error message logged by the Distribution Agent. If a session did not end in an error, this field is blank.  
  
 **Action Message**  
 All informational messages and error messages that the Distribution Agent has logged during the selected session.  
  
 **Action Time**  
 The time at which the action described in the **Action Message** column was performed.  
  
 **Error details or message of the selected session**  
 Displayed only if the selected session displays a value of **Error** in the **Status** column. This text area displays detailed error information and the command that was attempted at the time of the error. It also includes links to additional content related to the error.  
  
## See Also  
 [Start the Replication Monitor](../../Topics/TopicNameNotContainA/Start-the-Replication-Monitor.md)   
 [View Information and Perform Tasks for the Agents Associated With a Subscription (Replication Monitor)](../../Topics/TopicNameContainA/View-Information-and-Perform-Tasks-for-the-Agents-Associated-With-a-Subscription--Replication-Monitor-.md)   
 [Monitoring Replication](../../Topics/TopicNameNotContainA/Monitoring-Replication.md)   
 [Replication Agents Overview](../../Topics/TopicNameNotContainA/Replication-Agents-Overview.md)