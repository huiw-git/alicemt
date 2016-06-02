---
title: Set the Max Degree of Parallelism Option for Optimal Performance
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
---
# Set the Max Degree of Parallelism Option for Optimal Performance
  This rule determines whether the max degree of parallelism \(MAXDOP\) option for a value greater than 8. Setting this option to a larger value often causes unwanted resource consumption and performance degradation.  
  
## Best Practices Recommendations  
 Set the max degree of parallelism option to 8 or less by using sp\_configure.  
  
## For More Information  
 [Microsoft Knowledge Base article 329204](http://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configure the max degree of parallelism Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-max-degree-of-parallelism-Server-Configuration-Option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
  