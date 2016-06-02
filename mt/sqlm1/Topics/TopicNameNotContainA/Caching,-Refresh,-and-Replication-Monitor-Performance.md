---
title: Caching, Refresh, and Replication Monitor Performance
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
---
# Caching, Refresh, and Replication Monitor Performance
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Monitor is designed to efficiently monitor a large number of computers in a production system. The queries that Replication Monitor uses to perform calculations and gather data are cached and refreshed on a periodic basis. Caching reduces the number of queries and calculations required as you view different pages in Replication Monitor and allows monitoring to scale well for multiple users.  
  
 Cache refresh is handled by a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job, the **Replication monitoring refresher for distribution**. The job runs continuously, but the cache refresh schedule is based on waiting a certain amount time after the previous refresh:  
  
-   If there were agent history changes since the cache was last created, the wait time is the minimum of: 4 seconds; or the amount of time taken to create the previous cache.  
  
-   If there were no agent history changes since the cache was last created \(there could have been other changes\), the wait time is the maximum of: 30 seconds; or the amount of time taken to create the previous cache.  
  
## Refreshing the Replication Monitor User Interface  
 The Replication Monitor user interface can be refreshed in the following ways:  
  
-   The main Replication Monitor window \(including all tabs\), automatically refreshes by default every five seconds. Automatic refreshes do not force a refresh of the cache; the user interface displays the most recent version of the data from the cache. You can customize the refresh rate used for all windows associated with a Publisher by editing the Publisher settings. You can also disable automatic refreshes for a Publisher.  
  
-   The detail windows that are launched from Replication Monitor are not automatically refreshed by default, with the exception of windows related to merge subscriptions that are synchronizing. If you specify that detail windows should automatically refresh, they refresh on the same schedule as the main Replication Monitor window.  
  
-   All windows can be manually refreshed by pressing F5 or by right\-clicking a node in the Replication Monitor tree and clicking **Refresh**. Manual refreshes force a refresh of the cache.  
  
 For more information, see [Refresh Data in Replication Monitor](../../Topics\TopicNameNotContainA/Refresh-Data-in-Replication-Monitor.md).  
  
## Performance Considerations  
 Although Replication Monitor is designed to run efficiently, be aware of the following:  
  
-   If you have a large number of publications or subscriptions, consider setting a less frequent automatic refresh schedule for the user interface.  
  
-   Avoid concurrently running multiple instances of Replication Monitor.  
  
-   Avoid registering a large number of Distributors and setting Replication Monitor to automatically connect to all of them.  
  
## See Also  
 [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../Topic/Run%20Replication%20Maintenance%20Jobs%20\(SQL%20Server%20Management%20Studio\).md)   
 [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md)  
  
  