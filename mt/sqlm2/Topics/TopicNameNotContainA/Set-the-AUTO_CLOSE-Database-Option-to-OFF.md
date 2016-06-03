---
title: Set the AUTO_CLOSE Database Option to OFF
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
---
# Set the AUTO_CLOSE Database Option to OFF
  This rule checks whether the AUTO\_ CLOSE option is set OFF. When AUTO\_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection. AUTO\_CLOSE also flushes the procedure cache after each connection.  
  
## Best Practices Recommendations  
 If a database is accessed frequently, set the AUTO\_CLOSE option to OFF for the database.  
  
## For More Information  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  