---
title: Subscription Expiration and Deactivation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
---
# Subscription Expiration and Deactivation
  Subscriptions can be deactivated or can expire if they are not synchronized within a specified *retention period*. The action that occurs depends on the type of replication and the retention period that is exceeded.  
  
 To set retention periods, see [Set the Expiration Period for Subscriptions](../../Topics\TopicNameNotContainA/Set-the-Expiration-Period-for-Subscriptions.md), [Set the Distribution Retention Period for Transactional Publications &#40;SQL Server Management Studio&#41;](../Topic/Set%20the%20Distribution%20Retention%20Period%20for%20Transactional%20Publications%20\(SQL%20Server%20Management%20Studio\).md), and [Configure Publishing and Distribution](../../Topics\TopicNameNotContainA/Configure-Publishing-and-Distribution.md).  
  
## Transactional Replication  
 Transactional replication uses the maximum distribution retention period \(the **@max\_distretention** parameter of [sp_adddistributiondb &#40;Transact-SQL&#41;](../Topic/sp_adddistributiondb%20\(Transact-SQL\).md)\) and the publication retention period \(the **@retention** parameter of [sp_addpublication &#40;Transact-SQL&#41;](../Topic/sp_addpublication%20\(Transact-SQL\).md)\):  
  
-   If a subscription is not synchronized within the maximum distribution retention period \(default of 72 hours\) and there are changes in the distribution database that have not been delivered to the Subscriber, the subscription will be marked deactivated by the **Distribution clean up** job that runs on the Distributor. The subscription must be reinitialized.  
  
-   If a subscription is not synchronized within the publication retention period \(default of 336 hours\), the subscription will expire and be dropped by the **Expired subscription clean up** job that runs on the Publisher. The subscription must be recreated and synchronized.  
  
     If a push subscription expires, it is completely removed, but pull subscriptions are not. You must clean up pull subscriptions at the Subscriber. For more information, see [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md).  
  
## Merge Replication  
 Merge replication uses the publication retention period \(the **@retention** and **@retention\_period\_unit** parameters of [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md)\). When a subscription expires, it must be reinitialized, because metadata for the subscription is removed. Subscriptions that are not reinitialized are dropped by the **Expired subscription clean up** job that runs on the Publisher. By default, this job runs daily; it removes all push subscriptions that have not synchronized for double the length of the publication retention period. For example:  
  
-   If a publication has a retention period of 14 days, a subscription can expire if it has not synchronized within 14 days.  
  
     If the Publisher is running [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or a later version and the agent for the subscription is from [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] or a later version, a subscription only expires if there have been changes to the data in that subscription's partition. For example, suppose a Subscriber receives customer data only for customers in Germany. If the retention period is set to 14 days, the subscription expires on day 14 only if there have been changes to the German customer data in the last 14 days.  
  
-   From 14 days to 27 days after the last synchronization, the subscription can be reinitialized.  
  
-   At 28 days after the last synchronization, the subscription is dropped by the **Expired subscription clean up** job. If a push subscription expires, it is completely removed, but pull subscriptions are not. You must clean up pull subscriptions at the Subscriber. For more information, see [Delete a Pull Subscription](../../Topics\TopicNameContainA/Delete-a-Pull-Subscription.md).  
  
### Considerations for Setting the Publication Retention Period for Merge Publications  
 Keep the following considerations in mind when setting the retention period for merge publications:  
  
-   The retention period for merge publications has a 24\-hour grace period to accommodate Subscribers in different time zones. If, for example, you set a retention period of one day, the actual retention period is 48 hours.  
  
-   Cleanup of merge replication metadata is dependent on the publication retention period:  
  
    -   Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached. Use caution in specifying a high value for the retention period, because it can negatively impact replication performance. It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.  
  
    -   It is possible to specify that subscriptions never expire \(a value of 0 for **@retention**\), but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.  
  
-   The retention period for any republisher must be set to a value equal to or less than the retention period set at the original Publisher. You should also use the same publication retention values for all Publishers and their alternate synchronization partners. Using different values may lead to non\-convergence. If you need to change the publication retention value, reinitialize the Subscriber to avoid the non\-convergence of data.  
  
-   If, after a clean up, the publication retention period is increased and a subscription tries to merge with the Publisher \(which has already deleted the metadata\), the subscription will not expire because of the increased retention value. However, the Publisher does not have enough metadata to download changes to the Subscriber, which leads to non\-convergence.  
  
## See Also  
 [Reinitialize Subscriptions](../../Topics\TopicNameNotContainA/Reinitialize-Subscriptions.md)   
 [Replication Agent Administration](../../Topics\TopicNameNotContainA/Replication-Agent-Administration.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  