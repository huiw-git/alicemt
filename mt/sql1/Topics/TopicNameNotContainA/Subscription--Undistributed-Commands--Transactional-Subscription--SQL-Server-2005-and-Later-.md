---
title: "Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)
The **Undistributed Commands** tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands. For information about viewing the commands in the distribution database, see [Monitoring Replication with Replication Monitor](assetId:///199f5a74-e08e-4d02-a33c-b8ab0db20f44).  
  
## Options  
 **Number of commands in the distribution database waiting to be applied to this Subscriber**  
 The number of commands in the distribution database that have not been delivered to the selected Subscriber. A command consists of one Transact-SQL data manipulation language (DML) statement or one data definition language (DDL) statement.  
  
 **Estimated time to apply these commands, based on past performance**  
 The estimated amount of time to deliver commands to the Subscriber. If this value is greater than the amount of time required to generate and apply a snapshot to the Subscriber, consider reinitializing the Subscriber. For more information, see [Reinitialize Subscriptions](../../Topics/TopicNameNotContainA/Reinitialize-Subscriptions.md).  
  
## See Also  
 [Start the Replication Monitor](../../Topics/TopicNameNotContainA/Start-the-Replication-Monitor.md)   
 [Monitor Performance with Replication Monitor](../../Topics/TopicNameNotContainA/Monitor-Performance-with-Replication-Monitor.md)   
 [Monitoring Replication](../../Topics/TopicNameNotContainA/Monitoring-Replication.md)