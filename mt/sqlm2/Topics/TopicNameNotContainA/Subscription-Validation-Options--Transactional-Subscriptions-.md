---
title: Subscription Validation Options (Transactional Subscriptions)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
---
# Subscription Validation Options (Transactional Subscriptions)
  Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only, or a row count and a binary checksum.  
  
## Options  
 **Verify that the Subscriber has the same number of rows of replicated data as the Publisher**  
 Select the type of row count validation to perform. For Oracle publications, the only available option is **Compute an actual row count by querying the tables directly**.  
  
 **Compare checksums to verify row data**  
 In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm. If the row count fails, the checksum is not performed.  
  
 **Stop the Distribution Agent after the validation has completed**  
 By default, the Distribution Agent runs continuously. Select this option to stop the agent after validation is performed. This allows you to check whether validation was successful before continuing to replicate data to the Subscriber.  
  
## See Also  
 [Validate Data at the Subscriber](../../Topics\TopicNameNotContainA/Validate-Data-at-the-Subscriber.md)   
 [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md)  
  
  