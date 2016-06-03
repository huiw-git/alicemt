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
  This topic lists properties, system views, columns in system views, and wait types to support In\-Memory OLTP.  
  
|New or updated property, system view, stored procedures, or DMV|Change|  
|---------------------------------------------------------------------|------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../Topic/OBJECTPROPERTYEX%20\(Transact-SQL\).md)|**ExecIsWithNativeCompilation** and **TableIsMemoryOptimized** properties.<br /><br /> The **IsSchemaBound** property supports the Procedure object type \(returns 0 for procedures instead of NULL\).|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)|**IsXTPSupported** property.|  
|[sys.data_spaces &#40;Transact-SQL&#41;](../Topic/sys.data_spaces%20\(Transact-SQL\).md)|The following columns display additional values: **type** and **type\_desc**.|  
|[sys.indexes &#40;Transact-SQL&#41;](../Topic/sys.indexes%20\(Transact-SQL\).md)|The following columns display additional values: **type** and **type\_desc**.|  
|[sys.parameters &#40;Transact-SQL&#41;](../Topic/sys.parameters%20\(Transact-SQL\).md)|**is\_nullable** column.|  
|[sys.all_sql_modules &#40;Transact-SQL&#41;](../Topic/sys.all_sql_modules%20\(Transact-SQL\).md)|**uses\_native\_compilation** column.|  
|[sys.sql_modules &#40;Transact-SQL&#41;](../Topic/sys.sql_modules%20\(Transact-SQL\).md)|**uses\_native\_compilation** column.|  
|[sys.table_types &#40;Transact-SQL&#41;](../Topic/sys.table_types%20\(Transact-SQL\).md)|**is\_memory\_optimized** column.|  
|[sys.tables &#40;Transact-SQL&#41;](../Topic/sys.tables%20\(Transact-SQL\).md)|**durability**, **durability\_desc**, and **is\_memory\_optimized** columns.|  
|[sys.hash_indexes &#40;Transact-SQL&#41;](../Topic/sys.hash_indexes%20\(Transact-SQL\).md)|System view.|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_bind_db_resource_pool%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_checkpoint_force_garbage_collection%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_control_proc_exec_stats%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_control_query_exec_stats%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_merge_checkpoint_files%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_unbind_db_resource_pool%20\(Transact-SQL\).md)|Stored procedure.|  
|[sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_db_xtp_checkpoint_stats%20\(Transact-SQL\).md)||  
|[sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../Topic/sys.dm_db_xtp_checkpoint_files%20\(Transact-SQL\).md)||  
|[Memory-Optimized Table Dynamic Management Views &#40;Transact-SQL&#41;](../Topic/Memory-Optimized%20Table%20Dynamic%20Management%20Views%20\(Transact-SQL\).md)|DMVs to support In\-Memory OLTP.|  
  
## Wait Types  
 The following wait types support In\-Memory OLTP:  
  
-   WAIT\_XTP\_CKPT\_CLOSE  
  
-   WAIT\_XTP\_CKPT\_ENABLED  
  
-   WAIT\_XTP\_CKPT\_STATE\_LOCK  
  
-   WAIT\_XTP\_GUEST  
  
-   WAIT\_XTP\_HOST\_WAIT  
  
-   WAIT\_XTP\_OFFLINE\_CKPT\_LOG\_IO  
  
-   WAIT\_XTP\_OFFLINE\_CKPT\_NEW\_LOG  
  
-   WAIT\_XTP\_PROCEDURE\_ENTRY  
  
-   WAIT\_XTP\_TASK\_SHUTDOWN  
  
-   WAIT\_XTP\_TRAN\_COMMIT  
  
-   WAIT\_XTP\_TRAN\_DEPENDENCY  
  
-   XTPPROC\_CACHE\_ACCESS  
  
-   XTPPROC\_PARTITIONED\_STACK\_CREATE  
  
 For more information, about these wait types, see [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_os_wait_stats%20\(Transact-SQL\).md).  
  
## See Also  
 [Transact-SQL Support for In-Memory OLTP](../../Topics\TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)  
  
  