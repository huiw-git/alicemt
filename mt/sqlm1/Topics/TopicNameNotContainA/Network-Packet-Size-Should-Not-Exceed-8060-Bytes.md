---
title: Network Packet Size Should Not Exceed 8060 Bytes
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
---
# Network Packet Size Should Not Exceed 8060 Bytes
  If the value specified for sp\_configure 'network packet size' or if the network packet size of any logged\-in user is more than 8060 bytes, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] performs different memory allocation operations. This can cause an increase in the process virtual address space that is not reserved for the buffer pool.  
  
## Best Practices Recommendations  
 The network packet size should not exceed 8060 bytes.  
  
## For More Information  
 [Microsoft Knowledge Base article 903002](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  