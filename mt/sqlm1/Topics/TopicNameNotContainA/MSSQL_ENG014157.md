---
title: MSSQL_ENG014157
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
---
# MSSQL_ENG014157
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14157|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.|  
  
## Explanation  
 A Subscriber must synchronize with the Publisher within the time specified in the publication retention period. If a Subscriber does not synchronize within this period, the subscription expires. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
## User Action  
 The subscription must be re\-created and initialized before the Subscriber can begin receiving data changes again:  
  
-   For information about creating subscriptions, see [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md).  
  
-   For information about initializing subscriptions, see [Initialize a Subscription](../../Topics\TopicNameContainA/Initialize-a-Subscription.md).  
  
 If the subscription database contains changes that have not been synchronized with the Publisher, you can use the [tablediff Utility](../../Topics\TopicNameNotContainA/tablediff-Utility.md) to determine which rows are different in the publication and subscription databases.  
  
 You can increase the publication retention period to avoid having subscriptions expire. Use caution in setting a high value, because this can result in more data and metadata being stored, which affects performance. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  