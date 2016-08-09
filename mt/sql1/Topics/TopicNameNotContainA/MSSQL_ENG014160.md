---
title: "MSSQL_ENG014160"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# MSSQL_ENG014160
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|14160|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|The threshold [%s:%s] for the publication [%s] has been set. One or more subscriptions to this publication have expired.|  
  
## Explanation  
 Replication lets you enable warnings for several conditions. This includes imminent subscription expiration. Subscriptions can expire if they are not synchronized within a specified *retention period*. For more information, see [Subscription Expiration and Deactivation](../../Topics/TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
 When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](assetId:///2c3615d8-4a1a-4162-b096-97aefe6ddc16), you specify a threshold that determines when a warning is triggered. When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log. Reaching a threshold can also trigger a SQL Server Agent alert. For more information, see [Set Thresholds and Warnings in Replication Monitor](../../Topics/TopicNameNotContainA/Set-Thresholds-and-Warnings-in-Replication-Monitor.md) and [Programmatically Monitor Replication](../../Topics/TopicNameNotContainA/Programmatically-Monitor-Replication.md).  
  
## User Action  
 The resolution for this issue depends on the reason the warning was raised:  
  
-   If the threshold has been exceeded, but the subscription has not yet expired, synchronize the subscription. For more information, see [Synchronize Data](../../Topics/TopicNameNotContainA/Synchronize-Data.md).  
  
-   If the agent has been running, but has not been replicating changes properly, this can cause the subscription to expire. For transactional replication, make sure that the Distribution Agent and Log Reader Agent are running. For merge replication, make sure the Merge Agent is running. For information about how to start these agents, see [Start and Stop a Replication Agent (SQL Server Management Studio)](../../Topics/TopicNameContainA/Start-and-Stop-a-Replication-Agent--SQL-Server-Management-Studio-.md) and [Programming Replication Agent Executables](assetId:///cba476df-d4ea-44c9-bb86-81488971e328).  
  
-   If the subscription has expired, it must either be reinitialized or dropped and re-created, depending on the type of subscription and how long it has been expired. For more information, see [Subscription Expiration and Deactivation](../../Topics/TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
## See Also  
 [Errors and Events Reference (Replication)](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)