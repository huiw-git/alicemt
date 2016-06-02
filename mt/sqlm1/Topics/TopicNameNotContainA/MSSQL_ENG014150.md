---
title: MSSQL_ENG014150
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
---
# MSSQL_ENG014150
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14150|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Replication\-%s: agent %s succeeded. %s|  
  
## Explanation  
 This message indicates that a replication agent has successfully finished running. Replication uses the following agents:  
  
-   The Snapshot Agent. This agent is used by all publications.  
  
-   The Log Reader Agent. This agent is used by all transactional publications.  
  
-   The Queue Reader Agent. This agent is used by transactional publications enabled for queued updating subscriptions.  
  
-   The Distribution Agent. This agent synchronizes subscriptions to transactional and snapshot publications.  
  
-   The Merge Agent. This agent synchronizes subscriptions to merge publications.  
  
-   Replication maintenance jobs.  
  
## User Action  
 The Log Reader Agent, Queue Reader Agent, and Distribution Agent typically run continuously, whereas the other agents typically run on demand or on a schedule. If you do not expect an agent to have completed a run, check the status of the agent. For more information, see [Monitor Replication Agents](../../Topics\TopicNameNotContainA/Monitor-Replication-Agents.md).  
  
## See Also  
 [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md)   
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md)   
 [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)   
 [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)   
 [Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md)   
 [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md)  
  
  