---
title: Identify Bottlenecks
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
---
# Identify Bottlenecks
  Simultaneous access to shared resources causes bottlenecks. In general, bottlenecks are present in every software system and are inevitable. However, excessive demands on shared resources cause poor response time and must be identified and tuned.  
  
 Causes of bottlenecks include:  
  
-   Insufficient resources, requiring additional or upgraded components.  
  
-   Resources of the same type among which workloads are not distributed evenly; for example, one disk is being monopolized.  
  
-   Malfunctioning resources.  
  
-   Incorrectly configured resources.  
  
## Analyzing Bottlenecks  
 Excessive durations for various events are indicators of bottlenecks that can be tuned.  
  
 For example:  
  
-   Some other component may prevent the load from reaching this component thereby increasing the time to complete the load.  
  
-   Client requests may take longer due to network congestion.  
  
 Following are five key areas to monitor when tracking server performance to identify bottlenecks.  
  
|Possible bottleneck area|Effects on the server|  
|------------------------------|---------------------------|  
|Memory usage|Insufficient memory allocated or available to Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] degrades performance. Data must be read from the disk rather than directly from the data cache. Microsoft Windows operating systems perform excessive paging by swapping data to and from the disk as the pages are needed.|  
|CPU utilization|A chronically high CPU utilization rate may indicate that [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries need to be tuned or that a CPU upgrade is needed.|  
|Disk input\/output \(I\/O\)|[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries can be tuned to reduce unnecessary I\/O; for example, by employing indexes.|  
|User connections|Too many users may be accessing the server simultaneously causing performance degradation.|  
|Blocking locks|Incorrectly designed applications can cause locks and hamper concurrency, thus causing longer response times and lower transaction throughput rates.|  
  
## See Also  
 [Monitor CPU Usage](../../Topics\TopicNameNotContainA/Monitor-CPU-Usage.md)   
 [Monitor Disk Usage](../../Topics\TopicNameNotContainA/Monitor-Disk-Usage.md)   
 [Monitor Memory Usage](../../Topics\TopicNameNotContainA/Monitor-Memory-Usage.md)   
 [SQL Server, General Statistics Object](../../Topics\TopicNameNotContainA/SQL-Server,-General-Statistics-Object.md)   
 [SQL Server, Locks Object](../../Topics\TopicNameNotContainA/SQL-Server,-Locks-Object.md)  
  
  