---
title: "New and Updated Properties, System Views, Stored Procedures, Wait Types, and DMVs for In-Memory OLTP"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
robots: noindex,nofollow
---
# New and Updated Properties, System Views, Stored Procedures, Wait Types, and DMVs for In-Memory OLTP
This topic lists properties, system views, columns in system views, and wait types to support In-Memory OLTP.  
  
|New or updated property, system view, stored procedures, or DMV|Change|  
|---------------------------------------------------------------------|------------|  
|[OBJECTPROPERTYEX (Transact-SQL)](assetId:///be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd)|**ExecIsWithNativeCompilation** and **TableIsMemoryOptimized** properties.<br /><br /> The **IsSchemaBound** property supports the Procedure object type (returns 0 for procedures instead of NULL).|  
|[SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)|**IsXTPSupported** property.|  
|[sys.data_spaces (Transact-SQL)](assetId:///f39d55fe-2c0f-472d-a77f-cebc6fea95b5)|The following columns display additional values: **type** and **type_desc**.|  
|[sys.indexes (Transact-SQL)](assetId:///066bd9ac-6554-4297-88fe-d740de1f94a8)|The following columns display additional values: **type** and **type_desc**.|  
|[sys.parameters (Transact-SQL)](assetId:///24e2764b-c8e5-4322-97a4-7407d8b8a92b)|**is_nullable** column.|  
|[sys.all_sql_modules (Transact-SQL)](assetId:///7477a3fe-afb3-44c8-bb2c-c6e1d9bdee6f)|**uses_native_compilation** column.|  
|[sys.sql_modules (Transact-SQL)](assetId:///23d3ccd2-f356-4d89-a2cd-bee381243f99)|**uses_native_compilation** column.|  
|[sys.table_types (Transact-SQL)](assetId:///c05fd873-aff2-4a89-9936-a54c2ea09996)|**is_memory_optimized** column.|  
|[sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090)|**durability**, **durability_desc**, and **is_memory_optimized** columns.|  
|[sys.hash_indexes](assetId:///d9e230fb-d3ff-486f-86ef-44898f0a703e)|System view.|  
|[sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](assetId:///c2a78073-626b-4159-996e-1808f6bfb6d2)|Stored procedure.|  
|[sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)](assetId:///82b35b2b-edbd-44ac-9fc8-80695f2fd1df)|Stored procedure.|  
|[sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](assetId:///f5119808-76a1-4522-8529-9e02ee39adcb)|Stored procedure.|  
|[sys.sp_xtp_control_query_exec_stats (Transact-SQL)](assetId:///4838125d-ad1e-479e-b7d2-42655e8f4f02)|Stored procedure.|  
|[sys.sp_xtp_merge_checkpoint_files](assetId:///da04df2a-f7a1-41e7-a1ef-2d5d68919892)|Stored procedure.|  
|[sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)](assetId:///695a796d-087e-4bc8-99d0-ddc342604c75)|Stored procedure.|  
|[sys.dm_db_xtp_checkpoint_stats (Transact-SQL)](assetId:///8d0b18ca-db4d-4376-9905-3e4457727c46)||  
|[sys.dm_db_xtp_checkpoint_files (Transact-SQL)](assetId:///ac8e6333-7a9f-478a-b446-5602283e81c9)||  
|[Memory-Optimized Table Dynamic Management Views](assetId:///ccd82fed-1a3f-47de-85c4-1c9bdd80b027)|DMVs to support In-Memory OLTP.|  
  
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
  
 For more information, about these wait types, see [sys.dm_os_wait_stats (Transact-SQL)](assetId:///568d89ed-2c96-4795-8a0c-2f3e375081da).  
  
## See Also  
 [Transact-SQL Support for In-Memory OLTP](../../Topics/TopicNameNotContainA/Transact-SQL-Support-for-In-Memory-OLTP.md)