---
title: Types of Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
---
# Types of Replication
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides the following types of replication for use in distributed applications:  
  
-   Transactional replication. For more information, see [Transactional Replication](../../Topics\TopicNameNotContainA/Transactional-Replication.md).  
  
-   Merge replication. For more information, see [Merge Replication](../../Topics\TopicNameNotContainA/Merge-Replication.md).  
  
-   Snapshot replication. For more information, see [Snapshot Replication](../../Topics\TopicNameNotContainA/Snapshot-Replication.md).  
  
 The type of replication you choose for an application depends on many factors, including the physical replication environment, the type and quantity of data to be replicated, and whether the data is updated at the Subscriber. The physical environment includes the number and location of computers involved in replication and whether these computers are clients \(workstations, laptops, or handheld devices\) or servers.  
  
 Each type of replication typically begins with an initial synchronization of the published objects between the Publisher and Subscribers. This initial synchronization can be performed by replication with a *snapshot*, which is a copy of all of the objects and data specified by a publication. After the snapshot is created, it is delivered to the Subscribers. For some applications, snapshot replication is all that is required. For other types of applications, it is important that subsequent data changes flow to the Subscriber incrementally over time. Some applications also require that changes flow from the Subscriber back to the Publisher. Transactional replication and merge replication provide options for these types of applications.  
  
 Data changes are not tracked for snapshot replication; each time a snapshot is applied, it completely overwrites the existing data. Transactional replication tracks changes through the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] transaction log, and merge replication tracks changes through triggers and metadata tables.  
  
## See Also  
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)  
  
  