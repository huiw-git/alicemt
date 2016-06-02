---
title: Disable Lightweight Pooling
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
---
# Disable Lightweight Pooling
  This rule checks that lightweight pooling is disabled on the server. Setting lightweightpooling to 1 causes [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to switch to fiber mode scheduling. Fiber mode is intended for certain situations in which the context switching of the UMS workers is the important bottleneck in performance. Because this is rare, fiber mode seldom improves performance or scalability on the typical system.  
  
## Best Practices Recommendations  
 The lightweightpooling option should only be enabled after thorough testing, after all other performance tuning opportunities are evaluated, and when context switching is a known issue in your environment.  
  
 We recommend that you do not use fiber mode scheduling for routine operation because it can decrease performance by preventing the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that use Thread Local Storage \(TLS\) or thread\-owned objects, such as mutexes \(a kind of Win32 kernel object\), cannot function correctly in fiber mode  
  
 To remove lightweight pooling, execute the following statement, and then restart the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## For More Information  
 [lightweight pooling Server Configuration Option](../../Topics\TopicNameNotContainA/lightweight-pooling-Server-Configuration-Option.md)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  