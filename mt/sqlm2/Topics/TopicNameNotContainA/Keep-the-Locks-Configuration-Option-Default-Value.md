---
title: Keep the Locks Configuration Option Default Value
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
---
# Keep the Locks Configuration Option Default Value
  This rule checks the value of the locks configuration option. This option determines the maximum number of available locks. This limits how much memory the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] uses for locks. The default setting of 0 enables the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.  
  
 If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.  
  
## Best Practices Recommendations  
 Use the sp\_configure system stored procedure to change the value of locks to its default setting by using the following statement:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## For More Information  
 [Configure the locks Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-locks-Server-Configuration-Option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../Topic/sys.dm_tran_locks%20\(Transact-SQL\).md)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_os_wait_stats%20\(Transact-SQL\).md)  
  
 [Microsoft Knowledge Base article 271509](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## See Also  
 [Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)  
  
  