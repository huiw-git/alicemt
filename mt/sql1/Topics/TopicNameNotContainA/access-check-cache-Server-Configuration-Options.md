---
title: "access check cache Server Configuration Options"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# access check cache Server Configuration Options
When database objects are accessed by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the access check is cached in an internal structure called the **access check result cache**. The **access check cache quota** and **access check cache bucket count** options control the number of entries and number of hash buckets used for **access check result cache**. In rare circumstances, performance can be improved by changing these options.  
  
 The default values of 0 indicates that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is managing these options. Microsoft recommends only changing these options when directed by Microsoft Customer Support Services.  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)