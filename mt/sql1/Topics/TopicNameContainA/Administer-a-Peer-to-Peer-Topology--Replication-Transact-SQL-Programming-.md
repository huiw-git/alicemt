---
title: "Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)
Administering a peer-to-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations. The principal difference in administering a peer-to-peer topology is that some changes require the system to be *quiesced*. Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes. For more information, see [Quiesce a Replication Topology (Replication Transact-SQL Programming)](../../Topics/TopicNameContainA/Quiesce-a-Replication-Topology--Replication-Transact-SQL-Programming-.md).  
  
> [!NOTE]  
>  In a peer-to-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] than a pull subscriber.  
  
### To add an article to an existing configuration  
  
1.  Quiesce the system.  
  
2.  Stop the Distribution Agent at each node in the topology. For more information, see [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328) or [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md).  
  
3.  Execute the CREATE TABLE statement to add the new table at each node in the topology.  
  
4.  Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../Topics/TopicNameNotContainA/bcp-Utility.md).  
  
5.  Execute [sp_addarticle](assetId:///0483a157-e403-4fdb-b943-23c1b487bef0) to create the new article at each node in the topology. For more information, see [Define an Article](../../Topics/TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  After [sp_addarticle](assetId:///0483a157-e403-4fdb-b943-23c1b487bef0) is executed, replication automatically adds the article to the subscriptions in the topology.  
  
6.  Restart the Distribution Agents at each node in the topology.  
  
### To make schema changes to a publication database  
  
1.  Quiesce the system.  
  
2.  Execute the data definition language (DDL) statements to modify the schema of published tables. For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../../Topics/TopicNameNotContainA/Make-Schema-Changes-on-Publication-Databases.md).  
  
3.  Before you resume activity on published tables, quiesce the system again. This ensures that schema changes have been received by all nodes before any new data changes are replicated.  
  
## Example  
 The following example demonstrates how to add a new table article to an existing peer-to-peer replication topology that has two nodes.  
  
 [!CODE [HowTo#sp_addp2particle_createtables](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_createtables)]  
  
 [!CODE [HowTo#sp_addp2particle_cmdline](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_cmdline)]  
  
 [!CODE [HowTo#sp_addp2particle_createarticle](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_createarticle)]  
  
## See Also  
 [Administration (Replication)](../../Topics/TopicNameNotContainA/Administration--Replication-.md)   
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Peer-to-Peer Transactional Replication](../../Topics/TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)