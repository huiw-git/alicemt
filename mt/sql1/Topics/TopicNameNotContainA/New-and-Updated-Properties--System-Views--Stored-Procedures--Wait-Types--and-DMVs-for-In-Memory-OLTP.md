---
title: New and Updated Properties, System Views, Stored Procedures, Wait Types, and DMVs for In-Memory OLTP
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
robots: noindex,nofollow
---
# New and Updated Properties, System Views, Stored Procedures, Wait Types, and DMVs for In-Memory OLTP
  This topic lists properties, system views, columns in system views, and wait types to support In-Memory OLTP.  
  
|New or updated property, system view, stored procedures, or DMV|Change|  
|---------------------------------------------------------------------|------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../Topic/OBJECTPROPERTYEX%20\(Transact-SQL\).md)|**ExecIsWithNativeCompilation** and **TableIsMemoryOptimized** properties.<br /><br /> The **IsSchemaBound** property supports the Procedure object type (returns 0 for procedures instead of NULL).|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)|**IsXTPSupported** property.|  
|[sys.data_spaces &#40;Transact-SQL&#41;](../Topic/sys.data_spaces%20\(Transact-SQL\).md)|The following columns display additional values: **type** and **type_desc**.|  
|[sys.indexes &#40;Transact-SQL&#41;](../Topic/sys.indexes%20\(Transact-SQL\).md)|The following columns display additional values: **type** and **type_desc**.|  
|[sys.parameters &#40;Transact-SQL&#41;](../Topic/sys.parameters%20\(Transact-SQL\).md)|**is_nullable** column.|  
|[sys.all_sql_modules &#40;Transact-SQL&#41;](../Topic/sys.all_sql_modules%20\(Transact-SQL\).md)|**uses_native_compilation** column.|  
|[sys.sql_modules &#40;Transact-SQL&#41;](../Topic/sys.sql_modules%20\(Transact-SQL\).md)|**uses_native_compilation** column.|  
|[sys.table_types &#40;Transact-SQL&#41;](../Topic/sys.table_types%20\(Transact-SQL\).md)|**is_memory_optimized** column.|  
|[sys.tables &#40;Transact-SQL&#41;](../Topic/sys.tables%20\(Transact-SQL\).md)|**durability**, **durability_desc**, and **is_memory_optimized** columns.|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](../Topic/sys.hash_indexes%20\(Transact-SQL\).md)|System view.|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_bind_db_resource_pool%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_checkpoint_force_garbage_collection%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_control_proc_exec_stats%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_control_query_exec_stats%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_merge_checkpoint_files%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_unbind_db_resource_pool%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_db_xtp_checkpoint_stats%20\(Transact-SQL\).md)||  
|[sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../Topic/sys.dm_db_xtp_checkpoint_files%20\(Transact-SQL\).md)||  
|[Memory-Optimized Table Dynamic Management Views &#40;Transact-SQL&#41;](../Topic/Memory-Optimized%20Table%20Dynamic%20Management%20Views%20\(Transact-SQL\).md)|DMVs to support In-Memory OLTP.|  
  
## Wait Types  
 The following wait types support In-Memory OLTP:  
  
-   WAIT_XTP_CKPT_CLOSE  
  
-   WAIT_XTP_CKPT_ENABLED  
  
-   WAIT_XTP_CKPT_STATE_LOCK  
  
-   WAIT_XTP_GUEST  
  
-   WAIT_XTP_HOST_WAIT  
  
-   WAIT_XTP_OFFLINE_CKPT_LOG_IO  
  
-   WAIT_XTP_OFFLINE_CKPT_NEW_LOG  
  
-   WAIT_XTP_PROCEDURE_ENTRY  
  
-   WAIT_XTP_TASK_SHUTDOWN  
  
-   WAIT_XTP_TRAN_COMMIT  
  
-   WAIT_XTP_TRAN_DEPENDENCY  
  
-   XTPPROC_CACHE_ACCESS  
  
-   XTPPROC_PARTITIONED_STACK_CREATE  
  
 For more information, about these wait types, see [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_os_wait_stats%20\(Transact-SQL\).md).  
  
## See Also  
 [Transact-SQL Support for In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)  
  
  