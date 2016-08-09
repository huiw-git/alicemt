---
title: "ft notify bandwidth Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# ft notify bandwidth Server Configuration Option
Use the **ft notify bandwidth** option to specify the size to which the pool of small memory buffers can grow. Small memory buffers are 64 kilobytes (KB) in size. The *max* parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a small buffer pool. If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a small buffer pool.  
  
 The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of small memory buffers. Upon request from the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained. If, however, the **min** value specified is zero, then all memory buffers are released.  
  
 Under certain circumstances the number of buffers currently allocated is less than the value specified by the **min** parameter.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)]  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [ft crawl bandwidth Server Configuration Option](../../Topics/TopicNameNotContainA/ft-crawl-bandwidth-Server-Configuration-Option.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)