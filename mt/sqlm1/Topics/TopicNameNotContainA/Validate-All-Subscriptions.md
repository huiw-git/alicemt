---
title: Validate All Subscriptions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
---
# Validate All Subscriptions
  Use the **Validate All Subscriptions** dialog box to specify that all subscriptions to a merge publication should be validated the next time the Merge Agent for each subscription runs. The results of validation are displayed in Replication Monitor. For more information, see [Validate Data at the Subscriber](../../Topics\TopicNameNotContainA/Validate-Data-at-the-Subscriber.md).  
  
 It is also possible to validate a single subscription by right\-clicking a subscription in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and clicking **Validate Subscription**.  
  
## Options  
 **Verify the row counts only**  
 Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher. This method does not validate that the content of the rows matches. Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.  
  
 **Verify the row counts and compare checksums to verify the row data**  
 In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm. If the row count fails, the checksum is not performed. This option is not valid for [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)].  
  
## See Also  
 [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md)  
  
  