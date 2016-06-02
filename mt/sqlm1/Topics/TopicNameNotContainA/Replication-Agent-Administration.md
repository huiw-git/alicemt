---
title: Replication Agent Administration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f27186b8-b1b2-4da0-8b2b-91f632c2ab7e
---
# Replication Agent Administration
  Replication agents carry out many of the tasks associated with replication, including creating copies of schema and data, detecting updates at the Publisher or Subscriber, and propagating changes between servers. By default, replication agents run under [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job steps. The agents are simply executables, so they can also be called directly from the command line and from batch scripts. Each replication agent supports a set of run\-time parameters used to control how it runs; these parameters are specified in an agent profile or on the command line.  
  
> [!IMPORTANT]  
>  By default, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service is disabled when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed unless you explicitly choose to autostart the service during installation.  
  
 Replication agent files are located under [!INCLUDE[ssInstallPathVar](../../Token\Other/ssInstallPathVar_md.md)]\\COM. The following table lists the replication executable names and file names. Click the link for an agent to view its parameter reference.  
  
|Agent Executable|File Name|  
|----------------------|---------------|  
|[Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md)|snapshot.exe|  
|[Replication Distribution Agent](../../Topics\TopicNameNotContainA/Replication-Distribution-Agent.md)|distrib.exe|  
|[Replication Log Reader Agent](../../Topics\TopicNameNotContainA/Replication-Log-Reader-Agent.md)|logread.exe|  
|[Replication Queue Reader Agent](../../Topics\TopicNameNotContainA/Replication-Queue-Reader-Agent.md)|qrdrsvc.exe|  
|[Replication Merge Agent](../../Topics\TopicNameNotContainA/Replication-Merge-Agent.md)|replmerg.exe|  
  
 In addition to replication agents, replication has a number of jobs that perform scheduled and on\-demand maintenance.  
  
 **To run agents and maintenance jobs**  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and Replication Monitor: [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../Topic/Start%20and%20Stop%20a%20Replication%20Agent%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   Replication programming: [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md)  
  
## Agent Profiles  
 When replication is configured, a set of agent profiles is installed on the Distributor. An agent profile contains a set of parameters that are used each time an agent runs: each agent logs in to the Distributor during its startup process and queries for the parameters in its profile. Replication provides a default profile for each agent and additional predefined profiles for the Log Reader Agent, Distribution Agent, and Merge Agent. In addition to the profiles provided, you can create profiles suited to your application requirements. For more information, see [Replication Agent Profiles](../../Topics\TopicNameNotContainA/Replication-Agent-Profiles.md).  
  
 For information about specifying command line parameters directly, see [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md).  
  
## Monitoring Replication Agents  
 Replication Monitor allows you to view information and perform tasks associated with each replication agent. The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:  
  
-   The following agents are associated with publications in Replication Monitor:  
  
    -   Snapshot Agent  
  
    -   Log Reader Agent  
  
    -   Queue Reader Agent  
  
     Access information and tasks associated with these agents through the **Agents** tab. For more information, see [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md).  
  
-   The following agents are associated with subscriptions in Replication Monitor:  
  
    -   Distribution Agent  
  
    -   Merge Agent  
  
     Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** \(available for each Publisher\) or the **All Subscriptions** tab \(available for each publication\). For more information, see [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
## Independent and Shared Agents  
 An independent agent is an agent that services one subscription. A shared agent services multiple subscriptions; if multiple subscriptions using the same shared agent need to synchronize, by default they wait in a queue, and the shared agent services them one at a time. Latency is reduced when using independent agents because the agent is ready whenever the subscription needs to be synchronized. Merge replication always uses independent agents, and transactional replication uses independent agents by default for publications created in the New Publication Wizard \(in previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], transactional replication used shared agents by default\).  
  
## Replication Maintenance Jobs  
 Replication uses the following jobs to perform scheduled and on\-demand maintenance.  
  
|Clean up job|Description|Default schedule|  
|------------------|-----------------|----------------------|  
|Agent History Clean Up: Distribution|Removes replication agent history from the distribution database.|Runs every ten minutes|  
|Distribution Clean Up: Distribution|Removes replicated transactions from the distribution database. Deactivates subscriptions that have not been synchronized within the maximum distribution retention period.|Runs every ten minutes|  
|Expired Subscription Clean Up|Detects and removes expired subscriptions from publication databases.|Runs every day at 1:00 A.M.|  
|Reinitialize Subscriptions Having Data Validation Failures|Detects all subscriptions that have data validation failures and marks them for reinitialization. The next time the Merge Agent or Distribution Agent runs, a new snapshot will be applied at the Subscribers.|No default schedule \(not enabled by default\).|  
|Replication Agents Checkup|Detects replication agents that are not actively logging history. It writes to the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows event log if a job step fails.|Runs every ten minutes.|  
|Replication monitoring refresher for distribution|Refreshes cached queries used by Replication Monitor..|Runs continuously.|  
  
## See Also  
 [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md)  
  
  