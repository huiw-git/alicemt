---
title: "Set the Max Degree of Parallelism Option for Optimal Performance"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Set the Max Degree of Parallelism Option for Optimal Performance
This rule determines whether the max degree of parallelism (MAXDOP) option for a value greater than 8. Setting this option to a larger value often causes unwanted resource consumption and performance degradation.  
  
## Best Practices Recommendations  
 Set the max degree of parallelism option to 8 or less by using sp_configure.  
  
## For More Information  
 [Microsoft Knowledge Base article 329204](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configure the max degree of parallelism Server Configuration Option](../../Topics/TopicNameNotContainA/Configure-the-max-degree-of-parallelism-Server-Configuration-Option.md)  
  
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)