---
title: Set the AUTO_SHRINK Database Option to OFF
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
---
# Set the AUTO_SHRINK Database Option to OFF
  This rule checks whether the AUTO\_SHRINK database option is set to OFF. Frequently shrinking and expanding a database can lead to physical fragmentation.  
  
## Best Practices Recommendations  
 Set the AUTO\_SHRINK database option to OFF. If you know that the space that you are reclaiming will not be needed in the future, you can reclaim the space by manually shrinking the database.  
  
## For More Information  
 Microsoft Knowledge Base article [315512](http://go.microsoft.com/fwlink/?linkid=117750)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  