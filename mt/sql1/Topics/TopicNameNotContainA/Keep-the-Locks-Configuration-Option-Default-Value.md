---
title: "Keep the Locks Configuration Option Default Value"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Keep the Locks Configuration Option Default Value
This rule checks the value of the locks configuration option. This option determines the maximum number of available locks. This limits how much memory the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] uses for locks. The default setting of 0 enables the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.  
  
 If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.  
  
## Best Practices Recommendations  
 Use the sp_configure system stored procedure to change the value of locks to its default setting by using the following statement:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## For More Information  
 [Configure the locks Server Configuration Option](../../Topics/TopicNameNotContainA/Configure-the-locks-Server-Configuration-Option.md)  
  
 [sys.dm_tran_locks (Transact-SQL)](assetId:///f0d3b95a-8a00-471b-9da4-14cb8f5b045f)  
  
 [sys.dm_os_wait_stats (Transact-SQL)](assetId:///568d89ed-2c96-4795-8a0c-2f3e375081da)  
  
 [Microsoft Knowledge Base article 271509](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics/TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)