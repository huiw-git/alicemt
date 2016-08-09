---
title: "PolyBase troubleshooting with dynamic management views"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-03-11
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-polybase
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce9078b7-a750-4f47-b23e-90b83b783d80
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
robots: noindex,nofollow
---
# PolyBase troubleshooting with dynamic management views
With PolyBase, SQL Server 2016 introduces a set of new DMVs for trouble-shooting PolyBase queries. The DMVs with the prefix ‘_distributed’ capture all operations related to the distributed execution of PolyBase queries. The DMVs with the prefix ‘_external’ capture operations external to SQL Server or involve consuming data from the external data source.  
  
## Catalog views  
 Use the catalog views listed here to manage PolyBase operations.  
  
|||  
|-|-|  
|View|Description|  
|[sys.external_tables (Transact-SQL)](assetId:///fac4720c-b679-4ab2-864b-ff7810a9b559)|Identifies external tables.|  
|[sys.external_data_sources (Transact-SQL)](assetId:///1016db6e-9950-4ae2-a004-bd4171e27359)|Identifies external data sources.|  
|[sys.external_file_formats (Transact-SQL)](assetId:///a89efb2c-0a3a-4b64-9284-6e93263e29ac)|Finds external file formats.|  
  
## Dynamic Management Views  
  
|||  
|-|-|  
|[sys.dm_exec_compute_node_errors (Transact-SQL)](assetId:///9a03c039-70e4-4974-95d8-d3fa45984ffb)|[sys.dm_exec_compute_node_status (Transact-SQL)](assetId:///b606f91f-3a08-4a4f-bb57-32ae155b3738)|  
|[sys.dm_exec_compute_nodes (Transact-SQL)](assetId:///0de4b7a4-401f-4e2d-9ab0-c54587e05154)|[sys.dm_exec_distributed_request_steps (Transact-SQL)](assetId:///1954541d-b716-4e03-8fcc-7022f428e01d)|  
|[sys.dm_exec_distributed_requests (Transact-SQL)](assetId:///c041d416-d8c6-435e-a563-6a310abd33e3)|[sys.dm_exec_distributed_sql_requests (Transact-SQL)](assetId:///d065dc01-35d4-472f-9554-53ac41e7d104)|  
|[sys.dm_exec_dms_services (Transact-SQL)](assetId:///6ac47eef-4293-46b8-8555-07a614837504)|[sys.dm_exec_dms_workers (Transact-SQL)](assetId:///f468da29-78c3-4f10-8a3c-17905bbf46f2)|  
|[sys.dm_exec_external_operations (Transact-SQL)](assetId:///d268217a-85b8-4b7f-9cd1-87865eba2be1)|[sys.dm_exec_external_work (Transact-SQL)](assetId:///7597d97b-1fde-4135-ac35-4af12968f300)|  
  
## Examples  
  
```  
-- PolyBase trouble-Shooting scenarios  
-- Pick up the query that took longest time  
select   
    execution_id,  
       st.text,  
       dr.total_elapsed_time  
FROM sys.dm_exec_distributed_requests  dr  
     cross apply sys.dm_exec_sql_text(sql_handle) st  
order by total_elapsed_time desc  
  
--  Get the execution steps for the query based on the DSQL Plan  
select execution_id, step_index, operation_type, distribution_type, location_type, status, total_elapsed_time, command   
from sys.dm_exec_distributed_request_steps where execution_id =  'QIDXX' order by total_elapsed_time desc  
  
-- Get the DMS steps for the DMS Move    
select execution_id, step_index, dms_step_index, status, type, bytes_processed, total_elapsed_time  
from sys.dm_exec_dms_workers where execution_id = 'QIDXX' order by total_elapsed_time desc    
  
-- Get the information about the external DMS operations  
select * from sys.dm_exec_external_work where execution_id = 'QIDXX' order by total_elapsed_time desc   
  
-- Get the information about MR jobs executed during the Hadoop push-down. It contains a row for each map-reduce   
-- job that is pushed down to Hadoop as part of running a PolyBase query against an external table  
select * from sys.dm_exec_external_operations  
  
-- Get information about the scale out cluster  
select * from sys.dm_exec_compute_nodes  
  
--shows IS_External which is the only way to tell that this is an external table.  
SELECT name, type, IS_External FROM sys.tables WHERE name='bands'  
  
```  
  
## See Also  
 [PolyBase T-SQL objects](../../Topics/TopicNameNotContainA/PolyBase-T-SQL-objects.md)   
 [PolyBase troubleshooting with dynamic management views](../../Topics/TopicNameNotContainA/PolyBase-troubleshooting-with-dynamic-management-views.md)