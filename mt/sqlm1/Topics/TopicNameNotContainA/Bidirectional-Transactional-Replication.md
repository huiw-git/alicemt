---
title: Bidirectional Transactional Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
---
# Bidirectional Transactional Replication
  Bidirectional transactional replication is a specific transactional replication topology that allows two servers to exchange changes with each other: each server publishes data and then subscribes to a publication with the same data from the other server. The **@loopback\_detection** parameter of [sp_addsubscription &#40;Transact-SQL&#41;](../Topic/sp_addsubscription%20\(Transact-SQL\).md) is set to TRUE to ensure that changes are only sent to the Subscriber and do not result in the change being sent back to the Publisher.  
  
 In [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions, this topology is also supported by peer\-to\-peer transactional replication, but bidirectional replication can provide improved performance.  
  
## See Also  
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)  
  
  