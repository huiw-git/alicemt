---
title: View Publication and Subscription Status in Replication Monitor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
---
# View Publication and Subscription Status in Replication Monitor
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Replication Monitor displays status information for publications and subscriptions:  
  
-   The status of a publication is determined by the highest priority status of its subscriptions. For example, if one subscription to a publication has an error and another has a performance issue, a status of error is displayed for the publication.  
  
-   The status of a subscription is determined by the status of the agents that service the subscription. For merge replication, this is the Merge Agent. For transactional replication, this is either the Log Reader Agent or the Distribution Agent \(the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used\). For snapshot replication, this is the Snapshot Agent or the Distribution Agent \(the higher priority status is displayed\).  
  
 Tables in the following sections list the possible status values for publications and subscriptions. Three of the status values are displayed only if a threshold is met or exceeded:  
  
-   Expiring subscription  
  
     This status value applies to all types of replication. For more information, see [Set Thresholds and Warnings in Replication Monitor](../../Topics\TopicNameNotContainA/Set-Thresholds-and-Warnings-in-Replication-Monitor.md).  
  
-   Performance critical  
  
     This status value applies to transactional replication and merge replication. For more information, see [Monitor Performance with Replication Monitor](../../Topics\TopicNameNotContainA/Monitor-Performance-with-Replication-Monitor.md).  
  
-   Long\-running merge  
  
     This status value applies to merge replication. For more information, see [Monitor Performance with Replication Monitor](../../Topics\TopicNameNotContainA/Monitor-Performance-with-Replication-Monitor.md).  
  
 In addition to publication and subscription status, merge replication provides article\-level statistics, which give detailed information about: how much longer a merge phase will take to complete; how much time was spent processing a given article; the type of connection a Subscriber is using; and other important information. The statistics are displayed in the Merge Agent window in Replication Monitor. Snapshot and transactional replication provide detailed information on Distribution Agent processing.  
  
 **To view publication and subscription status**  
  
-   Replication Monitor: [View Information and Perform Tasks for a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Publication%20\(Replication%20Monitor\).md) and [View Information and Perform Tasks for a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Subscription%20\(Replication%20Monitor\).md)  
  
 **To view detailed information for agents**  
  
-   Replication Monitor: [View Information and Perform Tasks for the Agents Associated With a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Publication%20\(Replication%20Monitor\).md) and [View Information and Perform Tasks for the Agents Associated With a Subscription &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20the%20Agents%20Associated%20With%20a%20Subscription%20\(Replication%20Monitor\).md).  
  
## Publication Status Values  
 The following table shows publication status values and their corresponding icons in priority order.  
  
|Status|Icon|  
|------------|----------|  
|Error|![UI icon: error](../../Images\Image\ImageNotContaina/repl_icon_error.gif "repl_icon_error")|  
|Performance critical|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Retrying failed command|![UI icon: replication agent retry](../../Images\Image\ImageNotContaina/repl_icon_retry.gif "repl_icon_retry")|  
|OK|none|  
  
## Subscription Status Values  
 The following tables show subscription status values and their corresponding icons in priority order. It is possible for a subscription to be in two states at the same time, such as **Expiring soon\/Expired** and **Retrying failed command**; the highest priority status is displayed.  
  
 The status values **Performance critical**, **Expiring soon\/Expired**, and **Uninitialized** are warnings. When a warning is displayed, Replication Monitor also displays whether an agent is running. For example, the status could be **Running, Performance critical**.  
  
### Transactional subscriptions  
  
|Status|Icon|  
|------------|----------|  
|Error|![UI icon: error](../../Images\Image\ImageNotContaina/repl_icon_error.gif "repl_icon_error")|  
|Performance critical|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Expiring soon\/Expired|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Uninitialized subscription|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Retrying failed command|![UI icon: replication agent retry](../../Images\Image\ImageNotContaina/repl_icon_retry.gif "repl_icon_retry")|  
|Not running|![UI icon: replication agent stopped](../../Images\Image\ImageNotContaina/repl_icon_stopped.gif "repl_icon_stopped")|  
|Running|![UI icon: replication agent running](../../Images\Image\ImageNotContaina/repl_icon_running.gif "repl_icon_running")|  
  
### Merge subscriptions  
  
|Status|Icon|  
|------------|----------|  
|Error|![UI icon: error](../../Images\Image\ImageNotContaina/repl_icon_error.gif "repl_icon_error")|  
|Performance critical|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Long\-running merge|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Expiring soon\/Expired|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Uninitialized subscription|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Retrying failed command|![UI icon: replication agent retry](../../Images\Image\ImageNotContaina/repl_icon_retry.gif "repl_icon_retry")|  
|Synchronizing|![UI icon: replication agent running](../../Images\Image\ImageNotContaina/repl_icon_running.gif "repl_icon_running")|  
|Not Synchronizing|![UI icon: replication agent stopped](../../Images\Image\ImageNotContaina/repl_icon_stopped.gif "repl_icon_stopped")|  
  
### Snapshot subscriptions  
  
|Status|Icon|  
|------------|----------|  
|Error|![UI icon: error](../../Images\Image\ImageNotContaina/repl_icon_error.gif "repl_icon_error")|  
|Expiring soon\/Expired|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Uninitialized subscription|![UI icon: warning](../../Images\Image\ImageNotContaina/repl_icon_warn.gif "repl_icon_warn")|  
|Retrying failed command|![UI icon: replication agent retry](../../Images\Image\ImageNotContaina/repl_icon_retry.gif "repl_icon_retry")|  
|Synchronizing|![UI icon: replication agent running](../../Images\Image\ImageNotContaina/repl_icon_running.gif "repl_icon_running")|  
|Not Synchronizing|![UI icon: replication agent stopped](../../Images\Image\ImageNotContaina/repl_icon_stopped.gif "repl_icon_stopped")|  
  
## See Also  
 [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md)  
  
  