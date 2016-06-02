---
title: High Availability Support for In-Memory OLTP databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
---
# High Availability Support for In-Memory OLTP databases
  Databases containing memory\-optimized tables, with or without native compiled stored procedures, are fully supported with Always On Availability Groups.  There is no difference in the configuration and support for databases which contain [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] objects as compared to those without.  
  
 When an in\-memory OLTP database is deployed in an Always On Availability Group configuration, changes to memory\-optimized tables on the primary replica are applied in memory to the tables on the secondary replicas, when REDO is applied. This means that failover to a secondary replica can be very quick, since the data is already in memory. In addition,  the tables are available for queries on secondary replicas that have been configured for read access.  
  
## Always On Availability Groups and In\-Memory OLTP Databases  
 Configuring databases with [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] components provides the following:  
  
-   **A fully integrated experience**   
    You can configure your databases containing memory\-optimized tables using the same wizard with the same level of support for both synchronous and asynchronous secondary replicas. Additionally, health monitoring is provided using the familiar Always On dashboard in SQL Server Management Studio.  
  
-   **Comparable Failover time**   
    Secondary replicas maintain the in\-memory state of the durable memory\-optimized tables. In the event of automatic or forced failover, the time to failover to the new primary is comparable to disk\-bases tables as no recovery is needed. Memory\-optimized tables created as SCHEMA\_ONLY are supported in this configuration. However changes to these tables are not logged and therefore no data will exist in these tables on the secondary replica.  
  
-   **Readable Secondary**   
    You can access and query memory\-optimized tables on the secondary replica if it has been configured for read access. In [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], the read timestamp on the secondary replica is in close synchronization with the read timestamp on the primary replica, which means that changes on the primary become visible on the secondary very quickly. This close synchronization behaviour is different from [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] In\-Memory OLTP.  
  
## Failover Clustering Instance \(FCI\) and In\-Memory OLTP Databases  
 To achieve high\-availability in a shared\-storage configuration, you can set up failover clustering on instances with one or more database with memory\-optimized tables. You need to consider the following factors as part of setting up an FCI.  
  
-   **Recovery Time Objective**   
    Failover time will likely to be higher as the memory\-optimized tables must be loaded into memory before the database is made available.  
  
-   **SCHEMA\_ONLY tables**   
    Be aware that SCHEMA\_ONLY tables will be empty with no rows after the failover. This is as designed and defined by the application. This is exactly the same behavior when you restart an [!INCLUDE[hek_2](../../Token\Other/hek_2_md.md)] database with one or more SCHEMA\_ONLY tables.  
  
## Support for transaction replication in In\-Memory OLTP  
 Tables acting as transactional replication subscribers, excluding Peer\-to\-peer transactional replication, can be configured as memory\-optimized tables. Other replication configurations are not compatible with memory\-optimized tables.  For more information see [Replication to Memory-Optimized Table Subscribers](../../Topics\TopicNameNotContainA/Replication-to-Memory-Optimized-Table-Subscribers.md).  
  
## See Also  
 [Always On Availability Groups \(SQL Server\)](../Topic/AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(AlwaysOn%20Availability%20Groups\).md)   
 [Replication to Memory-Optimized Table Subscribers](../../Topics\TopicNameNotContainA/Replication-to-Memory-Optimized-Table-Subscribers.md)  
  
  