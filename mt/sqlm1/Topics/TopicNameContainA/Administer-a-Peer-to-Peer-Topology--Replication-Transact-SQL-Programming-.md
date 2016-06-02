---
title: Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)
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
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
---
# Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)
  Administering a peer\-to\-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations. The principal difference in administering a peer\-to\-peer topology is that some changes require the system to be *quiesced*. Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes. For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Quiesce%20a%20Replication%20Topology%20\(Replication%20Transact-SQL%20Programming\).md).  
  
> [!NOTE]  
>  In a peer\-to\-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] than a pull subscriber.  
  
### To add an article to an existing configuration  
  
1.  Quiesce the system.  
  
2.  Stop the Distribution Agent at each node in the topology. For more information, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md).  
  
3.  Execute the CREATE TABLE statement to add the new table at each node in the topology.  
  
4.  Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../Topics\TopicNameNotContainA/bcp-Utility.md).  
  
5.  Execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md) to create the new article at each node in the topology. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
    > [!NOTE]  
    >  After [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md) is executed, replication automatically adds the article to the subscriptions in the topology.  
  
6.  Restart the Distribution Agents at each node in the topology.  
  
### To make schema changes to a publication database  
  
1.  Quiesce the system.  
  
2.  Execute the data definition language \(DDL\) statements to modify the schema of published tables. For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../../Topics\TopicNameNotContainA/Make-Schema-Changes-on-Publication-Databases.md).  
  
3.  Before you resume activity on published tables, quiesce the system again. This ensures that schema changes have been received by all nodes before any new data changes are replicated.  
  
## Example  
 The following example demonstrates how to add a new table article to an existing peer\-to\-peer replication topology that has two nodes.  
  
 [!CODE [HowTo#sp_addp2particle_createtables](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_createtables)]  
  
 [!CODE [HowTo#sp_addp2particle_cmdline](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_cmdline)]  
  
 [!CODE [HowTo#sp_addp2particle_createarticle](../CodeSnippet/SQL15/replication/howto#sp_addp2particle_createarticle)]  
  
## See Also  
 [Administration &#40;Replication&#41;](../Topic/Administration%20\(Replication\).md)   
 [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)   
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)  
  
  