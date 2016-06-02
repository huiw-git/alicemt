---
title: Publication Types for Transactional Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
---
# Publication Types for Transactional Replication
  Transactional replication offers three publication types:  
  
|Publication Type|Description|  
|----------------------|-----------------|  
|Standard transactional publication|Appropriate for topologies in which all data at the Subscriber is read\-only \(transactional replication does not enforce this at the Subscriber\).<br /><br /> Standard transactional publications are created by default when using Transact\-SQL or Replication Management Objects \(RMO\). When using the New Publication Wizard, they are created by selecting **Transactional publication** on the **Publication Type** page.<br /><br /> For more information about creating publications, see [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md).|  
|Transactional publication in a peer\-to\-peer topology|The characteristics of this publication type are:<br /><br /> \-Each location has identical data and acts as both a Publisher and Subscriber.<br /><br /> \-The same row can be changed only at one location at a time.<br /><br /> \-This topology is best suited for server environments requiring high availability and read scalability.<br /><br /> <br /><br /> For more information, see [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md).|  
  
## See Also  
 [Transactional Replication](../../Topics\TopicNameNotContainA/Transactional-Replication.md)  
  
  