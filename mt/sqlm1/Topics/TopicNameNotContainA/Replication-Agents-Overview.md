---
title: Replication Agents Overview
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a35ecd7d-f130-483c-87e3-ddc8927bb91b
---
# Replication Agents Overview
  Replication uses a number of standalone programs, called agents, to carry out the tasks associated with tracking changes and distributing data. By default, replication agents run as jobs scheduled under [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent must be running for the jobs to run. Replication agents can also be run from the command line and by applications that use Replication Management Objects \(RMO\). Replication agents can be administered from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Monitor and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
## SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent hosts and schedules the agents used in replication and provides an easy way to run replication agents. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent also controls and monitors operations outside of replication. For more information, see [Configure SQL Server Agent](../Topic/Configure%20SQL%20Server%20Agent.md).  
  
> [!IMPORTANT]  
>  By default, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service is disabled when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed unless you explicitly choose to autostart the service during installation. For more information about starting the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service, see [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md).  
  
## Snapshot Agent  
 The Snapshot Agent is typically used with all types of replication. It prepares schema and initial data files of published tables and other objects, stores the snapshot files, and records information about synchronization in the distribution database. The Snapshot Agent runs at the Distributor. For more information, see [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md).  
  
## Log Reader Agent  
 The Log Reader Agent is used with transactional replication. It moves transactions marked for replication from the transaction log on the Publisher to the distribution database. Each database published using transactional replication has its own Log Reader Agent that runs on the Distributor and connects to the Publisher \(the Distributor can be on the same computer as the Publisher\). For more information, see [Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md).  
  
## Distribution Agent  
 The Distribution Agent is used with snapshot replication and transactional replication. It applies the initial snapshot to the Subscriber and moves transactions held in the distribution database to Subscribers. The Distribution Agent runs at either the Distributor for push subscriptions or at the Subscriber for pull subscriptions. For more information, see [Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md).  
  
## Merge Agent  
 The Merge Agent is used with merge replication. It applies the initial snapshot to the Subscriber and moves and reconciles incremental data changes that occur. Each merge subscription has its own Merge Agent that connects to both the Publisher and the Subscriber and updates both. The Merge Agent runs at either the Distributor for push subscriptions or the Subscriber for pull subscriptions. By default, the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber. For more information, see [Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md).  
  
## Queue Reader Agent  
 The Queue Reader Agent is used with transactional replication with the queued updating option. The agent runs at the Distributor and moves changes made at the Subscriber back to the Publisher. Unlike the Distribution Agent and the Merge Agent, only one instance of the Queue Reader Agent exists to service all Publishers and publications for a given distribution database. For more information about the Queue Reader Agent, see [Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md). For more information about updatable subscriptions, see [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md).  
  
## Replication Maintenance Jobs  
 Replication has a number of maintenance jobs that perform scheduled and on\-demand maintenance. For more information, see [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md).  
  
## See Also  
 [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md)   
 [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../Topic/Run%20Replication%20Maintenance%20Jobs%20\(SQL%20Server%20Management%20Studio\).md)   
 [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md)   
 [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md)  
  
  