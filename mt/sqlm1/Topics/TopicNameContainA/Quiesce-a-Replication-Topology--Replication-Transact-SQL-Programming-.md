---
title: Quiesce a Replication Topology (Replication Transact-SQL Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
---
# Quiesce a Replication Topology (Replication Transact-SQL Programming)
  *Quiescing* a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes. This topic explains how to quiesce a replication topology, which is required for a number of administrative tasks, and how to ensure that a node has received all changes from other nodes.  
  
### To quiesce a transactional replication topology with read\-only subscriptions  
  
1.  Stop activity on all published tables at the Publisher.  
  
2.  At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](../Topic/sp_posttracertoken%20\(Transact-SQL\).md).  
  
3.  At the Publisher on the publication database, execute [sp\_helptracertokenhistory](../Topic/sp_helptracertokenhistory%20\(Transact-SQL\).md).  
  
4.  Ensure that each Subscriber has received the tracer token.  
  
### To quiesce a transactional replication topology with updatable subscriptions  
  
1.  Stop activity on all published tables at the Publisher and all Subscribers.  
  
2.  If any Subscribers use queued updating subscriptions:  
  
    1.  If the Queue Reader Agent is not running in continuous mode, run the agent. For more information about running agents, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
    2.  To verify that the queue is empty, execute [sp\_replqueuemonitor](../Topic/sp_replqueuemonitor%20\(Transact-SQL\).md) at each Subscriber.  
  
3.  At the Publisher on the publication database, execute [sp\_posttracertoken](../Topic/sp_posttracertoken%20\(Transact-SQL\).md).  
  
4.  At the Publisher on the publication database, execute [sp\_helptracertokenhistory](../Topic/sp_helptracertokenhistory%20\(Transact-SQL\).md).  
  
5.  Ensure that each Subscriber has received the tracer token.  
  
### To quiesce a peer\-to\-peer transactional replication topology  
  
1.  Stop activity on all published tables at all nodes.  
  
2.  Execute [sp\_requestpeerresponse](../Topic/sp_requestpeerresponse%20\(Transact-SQL\).md) on each publication database in the topology.  
  
3.  If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent. The Log Reader Agent must be started before the Distribution Agent. For more information about running agents, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
4.  Execute [sp\_helppeerresponses](../Topic/sp_helppeerresponses%20\(Transact-SQL\).md) on each publication database in the topology. Ensure that the result set contains responses from each of the other nodes.  
  
### To ensure a peer\-to\-peer node has received all prior changes  
  
1.  Execute [sp\_requestpeerresponse](../Topic/sp_requestpeerresponse%20\(Transact-SQL\).md) on the publication database at the node you are checking.  
  
2.  If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent. The Log Reader Agent must be started before the Distribution Agent. For more information about running agents, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
3.  Execute [sp\_helppeerresponses](../Topic/sp_helppeerresponses%20\(Transact-SQL\).md) on the publication database at the node you are checking. Ensure that the result set contains responses from each of the other nodes.  
  
### To quiesce a merge replication topology  
  
1.  Stop activity on all published tables at the Publisher and at all Subscribers.  
  
2.  Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time. This ensures that all changes are replicated to all nodes. For more information about running agents, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
    > [!NOTE]  
    >  If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.  
  
## See Also  
 [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Administer%20a%20Peer-to-Peer%20Topology%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Measure Latency and Validate Connections for Transactional Replication](../../Topics\TopicNameNotContainA/Measure-Latency-and-Validate-Connections-for-Transactional-Replication.md)  
  
  