---
title: "Set the AUTO_CLOSE Database Option to OFF"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Set the AUTO_CLOSE Database Option to OFF
This rule checks whether the AUTO_ CLOSE option is set OFF. When AUTO_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection. AUTO_CLOSE also flushes the procedure cache after each connection.  
  
## Best Practices Recommendations  
 If a database is accessed frequently, set the AUTO_CLOSE option to OFF for the database.  
  
## For More Information  
 [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)