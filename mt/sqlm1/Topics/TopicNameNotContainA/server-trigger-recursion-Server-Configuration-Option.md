---
title: server trigger recursion Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
---
# server trigger recursion Server Configuration Option
  Use the **server trigger recursion** option to specify whether to allow server\-level triggers to fire recursively. When this option is set to 1 \(ON\), server\-level triggers will be allowed to fire recursively. When set to 0 \(OFF\), server\-level triggers cannot be fired recursively. Only direct recursion is prevented when the server trigger recursion option is set to 0 \(OFF\). \(To disable indirect recursion, set the **nested triggers** option to 0.\) The default value for this option is 1 \(ON\). The setting takes effect immediately \(without a server restart\).  
  
 For more information, see [Create Nested Triggers](../../Topics\TopicNameNotContainA/Create-Nested-Triggers.md).  
  
## See Also  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  