---
title: Set the Expiration Period for Subscriptions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
---
# Set the Expiration Period for Subscriptions
  This topic describes how to set the expiration period for subscriptions in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. The expiration period for subscriptions determines the period of time before a subscription expires and is removed. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To set the expiration period for subscriptions, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   The subscription expiration period is also referred to as the *publication retention period*. Cleanup of merge replication metadata is dependent on this setting:  
  
    -   Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached. Use caution in specifying a high value for the retention period, because it can negatively impact replication performance. It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.  
  
         The retention period for merge publications has a 24\-hour grace period to accommodate Subscribers in different time zones. If, for example, you set a retention period of one day, the actual retention period is 48 hours.  
  
    -   It is possible to specify that subscriptions never expire, but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Set the expiration period for subscriptions on the **General** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To set the expiration period for subscriptions  
  
1.  In the **Subscription expiration** section on the **General** page of the **Publication Properties \- \<Publication\>** dialog box, specify whether subscriptions should expire.  
  
2.  If they should expire, specify an expiration time period.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 You can use replication stored procedures to either set this value when a publication is created or modify this value at a later time.  
  
#### To set the expiration period for a subscription to a snapshot or transactional publication  
  
1.  At the Publisher, execute [sp\_addpublication](../Topic/sp_addpublication%20\(Transact-SQL\).md). Specify the desired subscription expiration period, in hours, for **@retention**. The default expiration period is 336 hours. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
#### To set the expiration period for a subscription to a merge publication  
  
1.  At the Publisher, execute [sp\_addmergepublication](../Topic/sp_addmergepublication%20\(Transact-SQL\).md). Specify the desired value for the subscription expiration period for **@retention**. Specify the units in which the expiration period is expressed for **@retention\_period\_unit**, which can be one of the following:  
  
    -   **1** \= week  
  
    -   **2** \= month  
  
    -   **3** \= year  
  
     The default expiration period is 14 days. For more information, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
#### To change the expiration period for a subscription to a snapshot or transactional publication  
  
1.  At the Publisher, execute [sp\_changepublication](../Topic/sp_changepublication%20\(Transact-SQL\).md). Specify **retention** for **@property** and the new subscription expiration period, in hours, for **@value**.  
  
#### To change the expiration period for a subscription to a merge publication  
  
1.  At the Publisher, execute [sp\_helpmergepublication](../Topic/sp_helpmergepublication%20\(Transact-SQL\).md), specifying **@publication** and **@publisher**. Note the value of **retention\_period\_unit** in the result set, which can be one of the following:  
  
    -   **0** \= day  
  
    -   **1** \= week  
  
    -   **2** \= month  
  
    -   **3** \= year  
  
2.  At the Publisher, execute [sp\_changemergepublication](../Topic/sp_changemergepublication%20\(Transact-SQL\).md). Specify **retention** for **@property** and the new subscription expiration period, as text based on the retention period unit from step 1, for **@value**.  
  
3.  \(Optional\) At the Publisher, execute [sp\_changemergepublication](../Topic/sp_changemergepublication%20\(Transact-SQL\).md). Specify **retention\_period\_unit** for **@property** and a new unit for the subscription expiration period for **@value**.  
  
## See Also  
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md)  
  
  