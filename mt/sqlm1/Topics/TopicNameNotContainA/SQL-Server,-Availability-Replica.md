---
title: SQL Server, Availability Replica
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e402f996-c1fb-484a-b804-45c49972f2e0
---
# SQL Server, Availability Replica
  The **SQLServer:Availability Replica** performance object contains performance counters that report information about the availability replicas in Always On availability groups in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. All availability replica performance counters apply to both the primary replica and the secondary replicas, with send\/receive counters reflecting the local replica. For the most part, the primary replica sends most of the data, and the secondary replicas receive the data. However, secondary replicas send ACKs and some other background traffic to the primary replicas. Note that on a given availability replica, some counters will show a zero value, depending on the current role, primary or secondary, of the local replica.  
  
|Counter Name|Description|  
|------------------|-----------------|  
|**Bytes Received from Replica\/sec**|Number of bytes received from the availability replica per second. Pings and status updates will generate network traffic even on databases with no user updates.|  
|**Bytes Sent to Replica\/sec**|Number of bytes sent to the remote availability replica per second. On the primary replica this is the number of bytes sent to the secondary replica. On the secondary replica this is the number of bytes sent to the primary replica.|  
|**Bytes Sent to Transport\/sec**|Actual number of bytes sent per second over the network to the remote availability replica. On the primary replica this is the number of bytes sent to the secondary replica. On the secondary replica this is the number of bytes sent to the primary replica.|  
|**Flow Control Time \(ms\/sec\)**|Time in milliseconds that log stream messages waited for send flow control, in the last second.|  
|**Flow Control\/sec**|Number of times flow\-control initiated in the last second. **Flow Control Time \(ms\/sec\)** divided by **Flow Control\/sec** is the average time per wait.|  
|**Receives from Replica\/sec**|Number of Always On messages received from thereplica per second.|  
|**Resent Messages\/sec**|Number of Always On messages resent in the last second.|  
|**Sends to Replica\/sec**|Number of Always On messages sent to this availability replica per second.|  
|**Sends to Transport\/sec**|Actual number of Always On messages sent per second over the network to the remote availability replica. On the primary replica this is the number of messages sent to the secondary replica. On the secondary replica this is the number of messages sent to the primary replica.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [SQL Server, Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md)   
 [AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  