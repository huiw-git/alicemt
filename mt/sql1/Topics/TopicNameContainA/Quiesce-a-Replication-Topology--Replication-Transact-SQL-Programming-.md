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
  
### To quiesce a transactional replication topology with read-only subscriptions  
  
1.  Stop activity on all published tables at the Publisher.  
  
2.  At the Publisher on the publication database, execute [Measuring Latency and Validating Connections for Transactional Replication](assetId:///24da5cd2-1c45-475e-93db-5bdf660f1c2c).  
  
3.  At the Publisher on the publication database, execute [sp_helptracertokenhistory](assetId:///96910d1c-be76-43eb-9c93-4477e6761749).  
  
4.  Ensure that each Subscriber has received the tracer token.  
  
### To quiesce a transactional replication topology with updatable subscriptions  
  
1.  Stop activity on all published tables at the Publisher and all Subscribers.  
  
2.  If any Subscribers use queued updating subscriptions:  
  
    1.  If the Queue Reader Agent is not running in continuous mode, run the agent. For more information about running agents, see [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328) or [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
    2.  To verify that the queue is empty, execute [sp_replqueuemonitor](assetId:///6909a3f1-43a2-4df5-a6a5-9e6f347ac841) at each Subscriber.  
  
3.  At the Publisher on the publication database, execute [sp_posttracertoken](assetId:///24da5cd2-1c45-475e-93db-5bdf660f1c2c).  
  
4.  At the Publisher on the publication database, execute [sp_helptracertokenhistory](assetId:///96910d1c-be76-43eb-9c93-4477e6761749).  
  
5.  Ensure that each Subscriber has received the tracer token.  
  
### To quiesce a peer-to-peer transactional replication topology  
  
1.  Stop activity on all published tables at all nodes.  
  
2.  Execute [sp_requestpeerresponse](assetId:///cbe13c22-4d7d-4a36-b194-7a13ce68ef27) on each publication database in the topology.  
  
3.  If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent. The Log Reader Agent must be started before the Distribution Agent. For more information about running agents, see [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328) or [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
4.  Execute [sp_helppeerresponses](assetId:///e55789d1-43fb-4a37-9e5e-60ccef122a5d) on each publication database in the topology. Ensure that the result set contains responses from each of the other nodes.  
  
### To ensure a peer-to-peer node has received all prior changes  
  
1.  Execute [sp_requestpeerresponse](assetId:///cbe13c22-4d7d-4a36-b194-7a13ce68ef27) on the publication database at the node you are checking.  
  
2.  If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent. The Log Reader Agent must be started before the Distribution Agent. For more information about running agents, see [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328) or [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
3.  Execute [sp_helppeerresponses](assetId:///e55789d1-43fb-4a37-9e5e-60ccef122a5d) on the publication database at the node you are checking. Ensure that the result set contains responses from each of the other nodes.  
  
### To quiesce a merge replication topology  
  
1.  Stop activity on all published tables at the Publisher and at all Subscribers.  
  
2.  Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time. This ensures that all changes are replicated to all nodes. For more information about running agents, see [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328) or [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
    > [!NOTE]  
    >  If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.  
  
## See Also  
 [Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)](../../Topics/TopicNameContainA/Administer-a-Peer-to-Peer-Topology--Replication-Transact-SQL-Programming-.md)   
 [Measure Latency and Validate Connections for Transactional Replication](../../Topics/TopicNameNotContainA/Measure-Latency-and-Validate-Connections-for-Transactional-Replication.md)