---
title: Monitoring Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
---
# Monitoring Replication
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Monitor is a graphical tool that allows you to monitor the overall health of a replication topology. Replication Monitor provides detailed information on the status and performance of publications and subscriptions, allowing you to answer common questions, such as:  
  
-   Is my replication system healthy?  
  
-   Which subscriptions are slow?  
  
-   How far behind is my transactional subscription?  
  
-   How long will it take a transaction committed now to reach a Subscriber in transactional replication?  
  
-   Why is my merge subscription slow?  
  
-   Why is an agent not running?  
  
 To monitor replication, a user must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database. A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.  
  
## In This Section  
 The following topics provide information about Replication Monitor features.  
  
 [Overview of the Replication Monitor Interface](../../Topics\TopicNameNotContainA/Overview-of-the-Replication-Monitor-Interface.md)  
 Describes each window and tab in Replication Monitor and provides information on how to answer the questions listed above.  
  
 [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md)  
 Describes how to start the Replication Monitor.  
  
 [Allow Non-Administrators to Use Replication Monitor](../../Topics\TopicNameNotContainA/Allow-Non-Administrators-to-Use-Replication-Monitor.md)  
 Describes how to assign permissions to non\-administrators so that they can use Replication Monitor.  
  
 [Add and Remove Publishers from Replication Monitor](../../Topics\TopicNameNotContainA/Add-and-Remove-Publishers-from-Replication-Monitor.md)  
 Describes how to add or remove Publishers from Replication Monitor.  
  
 [Refresh Data in Replication Monitor](../../Topics\TopicNameNotContainA/Refresh-Data-in-Replication-Monitor.md)  
 Describes how to refresh data in Replication Monitor.  
  
 [Monitor Performance with Replication Monitor](../../Topics\TopicNameNotContainA/Monitor-Performance-with-Replication-Monitor.md)  
 Describes how to monitor performance in Replication Monitor, including information on setting performance thresholds. Includes information on article\-level statistics for merge replication, which provide a detailed view of processing.  
  
 [Measure Latency and Validate Connections for Transactional Replication](../../Topics\TopicNameNotContainA/Measure-Latency-and-Validate-Connections-for-Transactional-Replication.md)  
 Describes tracer tokens, which allow you to measure the performance of a transactional replication topology.  
  
 [Monitor Replication Agents](../../Topics\TopicNameNotContainA/Monitor-Replication-Agents.md)  
 Describes how to find information about each replication agent.  
  
 [Set Thresholds and Warnings in Replication Monitor](../../Topics\TopicNameNotContainA/Set-Thresholds-and-Warnings-in-Replication-Monitor.md)  
 Describes the warnings, thresholds, and alerts you can set in Replication Monitor. It is recommended that you enable warnings for your topology, so that you are informed about status and performance in a timely manner.  
  
 [Caching, Refresh, and Replication Monitor Performance](../../Topics\TopicNameNotContainA/Caching,-Refresh,-and-Replication-Monitor-Performance.md)  
 Describes how Replication Monitor caches data and calculations to improve performance; explains how refresh of the user interface relates to refresh of the cache.  
  
 [View Publication and Subscription Status in Replication Monitor](../../Topics\TopicNameNotContainA/View-Publication-and-Subscription-Status-in-Replication-Monitor.md)  
 Describes how to view status information a Publication or Subscription by using the Replication Monitor.  
  
 [View Information and Perform Tasks for a Publisher &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Publisher%20\(Replication%20Monitor\).md)  
 Describes how to view information and perform tasks for a Publisher by using the Replication Monitor.  
  
 [View Information and Perform Tasks for a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Publication%20\(Replication%20Monitor\).md)  
 Describes how to view information and perform tasks for a Publication by using the Replication Monitor.  
  
 [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md)  
 Describes how to view information and perform tasks for the agents associated with a Publication by using the Replication Monitor.  
  
 [View Information and Perform Tasks for a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Subscription%20\(Replication%20Monitor\).md)  
 Describes how to view information and perform tasks for a Subscription by using the Replication Monitor.  
  
 [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md)  
 Describes how to view information and perform tasks for the agents associated with a Subscription by using the Replication Monitor.  
  
  