---
title: Verify Max Worker Threads Setting
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
---
# Verify Max Worker Threads Setting
  This rule checks the max worker threads server option for potentially incorrect settings. Setting the max worker threads option to a small value may prevent enough threads from servicing incoming client requests in a timely manner and could lead to "thread starvation". However, setting the option to a large value can waste address space, because each active thread consumes up to 4 MB on 64\-bit servers.  
  
## Best Practices Recommendations  
 Set the max worker threads option to 0. This enables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to automatically determine the correct number of active worker threads based on user requests.  
  
## For More Information  
 [Configure the max worker threads Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-max-worker-threads-Server-Configuration-Option.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  