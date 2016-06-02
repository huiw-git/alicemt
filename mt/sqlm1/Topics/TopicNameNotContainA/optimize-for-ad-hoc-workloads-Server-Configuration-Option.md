---
title: optimize for ad hoc workloads Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
---
# optimize for ad hoc workloads Server Configuration Option
  The **optimize for ad hoc workloads** option is used to improve the efficiency of the plan cache for workloads that contain many single use ad hoc batches. When this option is set to 1, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] stores a small compiled plan stub in the plan cache when a batch is compiled for the first time, instead of the full compiled plan. This helps to relieve memory pressure by not allowing the plan cache to become filled with compiled plans that are not reused.  
  
 The compiled plan stub allows the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to recognize that this ad hoc batch has been compiled before but has only stored a compiled plan stub, so when this batch is invoked \(compiled or executed\) again, the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] compiles the batch, removes the compiled plan stub from the plan cache, and adds the full compiled plan to the plan cache.  
  
 Setting the **optimize for ad hoc workloads** to 1 affects only new plans; plans that are already in the plan cache are unaffected.  
  
 The compiled plan stub is one of the cacheobjtypes displayed by the sys.dm\_exec\_cached\_plans catalog view. It has a unique sql handle and plan handle. The compiled plan stub does not have an execution plan associated with it and querying for the plan handle will not return an XML Showplan.  
  
 Trace flag 8032 reverts the cache limit parameters to the [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] RTM setting which in general allows caches to be larger. Use this setting when frequently reused cache entries do not fit into the cache and when the optimize for ad hoc workloads Server Configuration Option has failed to resolve the problem with plan cache.  
  
> [!WARNING]  
>  Trace flag 8032 can cause poor performance if large caches make less memory available for other memory consumers, such as the buffer pool.  
  
## See Also  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../Topic/sys.dm_exec_cached_plans%20\(Transact-SQL\).md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  