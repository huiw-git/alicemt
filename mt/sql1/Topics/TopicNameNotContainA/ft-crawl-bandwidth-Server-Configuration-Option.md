---
title: "ft crawl bandwidth Server Configuration Option"
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
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# ft crawl bandwidth Server Configuration Option
Use the **ft crawl bandwidth** option to specify the size to which the pool of large memory buffers can grow. Large memory buffers are 4 megabytes (MB) in size. The **max** parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a large buffer pool. If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a large buffer pool.  
  
 The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of large memory buffers. Upon request from the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained. If, however, the **min** value specified is zero, then all memory buffers are released.  
  
 Under certain circumstances, the number of buffers currently allocated is less than the value specified by the **min** parameter.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureAvoid_md.md)]  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [ft notify bandwidth Server Configuration Option](../../Topics/TopicNameNotContainA/ft-notify-bandwidth-Server-Configuration-Option.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)