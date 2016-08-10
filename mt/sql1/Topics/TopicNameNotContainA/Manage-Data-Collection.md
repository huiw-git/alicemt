---
title: "Manage Data Collection"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# Manage Data Collection
You can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] stored procedures and functions to manage different aspects of data collection, such as enabling or disabling data collection, changing a collection set configuration, or viewing data in the management data warehouse.  
  
## Manage Data Collection by Using SQL Server Management Studio  
 You can perform the following data collector-related tasks by using Object Explorer in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]:  
  
-   [Configure the Management Data Warehouse (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Configure-the-Management-Data-Warehouse--SQL-Server-Management-Studio-.md)  
  
-   [Configure Properties of a Data Collector](../../Topics/TopicNameContainA/Configure-Properties-of-a-Data-Collector.md)  
  
-   [Enable or Disable Data Collection](../../Topics/TopicNameNotContainA/Enable-or-Disable-Data-Collection.md)  
  
-   [Start or Stop a Collection Set](../../Topics/TopicNameContainA/Start-or-Stop-a-Collection-Set.md)  
  
-   [Use SQL Server Profiler to Create a SQL Trace Collection Set (SQL Server Management Studio)](../../Topics/TopicNameContainA/Use-SQL-Server-Profiler-to-Create-a-SQL-Trace-Collection-Set--SQL-Server-Management-Studio-.md)  
  
-   [View Collection Set Logs (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-Collection-Set-Logs--SQL-Server-Management-Studio-.md)  
  
-   [View or Change Collection Set Schedules (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-or-Change-Collection-Set-Schedules--SQL-Server-Management-Studio-.md)  
  
-   [View a Collection Set Report (SQL Server Management Studio)](../../Topics/TopicNameContainA/View-a-Collection-Set-Report--SQL-Server-Management-Studio-.md)  
  
## Manage Data Collection by Using Transact-SQL  
 The data collector provides an extensive collection of stored procedures that you can use to perform any data-collector related task. For example, by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], you can perform the following tasks:  
  
-   [Configure Data Collection Parameters (Transact-SQL)](../../Topics/TopicNameNotContainA/Configure-Data-Collection-Parameters--Transact-SQL-.md)  
  
-   [Enable or Disable Data Collection](../../Topics/TopicNameNotContainA/Enable-or-Disable-Data-Collection.md)  
  
-   [Start or Stop a Collection Set](../../Topics/TopicNameContainA/Start-or-Stop-a-Collection-Set.md)  
  
-   [Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Custom-Collection-Set-That-Uses-the-Generic-T-SQL-Query-Collector-Type--Transact-SQL-.md)  
  
-   [Add a Collection Item to a Collection Set (Transact-SQL)](../../Topics/TopicNameContainA/Add-a-Collection-Item-to-a-Collection-Set--Transact-SQL-.md)  
  
 In addition, there are functions and views that you can use to get configuration data for the msdb and management data warehouse databases, execution log data, and data that is stored in the management data warehouse.  
  
 You can use the stored procedures, functions, and views that are provided to create your own end-to-end data collection scenarios.  
  
> [!IMPORTANT]  
>  Unlike regular stored procedures, the data collector stored procedures use strictly typed parameters and do not support automatic data type conversion. If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.  
  
 You can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] to create and execute the provided code samples. For more information, see [Using Object Explorer](assetId:///469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2). As an alternative you can create the query in any editor and save it in a text file that has a .sql file name extension. You can execute the query from the Windows command prompt using the **sqlcmd** utility. For more information, see [Use the sqlcmd Utility](../../Topics/TopicNameNotContainA/Use-the-sqlcmd-Utility.md).  
  
### Stored Procedures and Views  
 **Working with the data collector**  
  
 The following table describes the stored procedures that you can use to work with the data collector.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_enable_collector](assetId:///53ff2b0d-b7da-4e3d-8f3d-35e857bc3720)|Enable the data collector.|  
|[sp_syscollector_disable_collector](assetId:///9ef4c85d-cca6-452d-94be-2be6f616c3d8)|Disable the data collector.|  
  
 **Working with collection sets**  
  
 The following table describes the stored procedures that you can use to work with collection sets.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_run_collection_set](assetId:///7bbaee48-dfc7-45c0-b11f-c636b6a7e720)|Run a collection set on demand.|  
|[sp_syscollector_start_collection_set](assetId:///d8357180-f51e-4681-99f9-0596fe2d2b53)|Start a collection set.|  
|[sp_syscollector_stop_collection_set](assetId:///4668cfb7-462f-40d0-948c-8f740a792a4d)|Stop a collection set.|  
|[sp_syscollector_create_collection_set](assetId:///69e9ff0f-c409-43fc-89f6-40c3974e972c)|Create a collection set.|  
|[sp_syscollector_delete_collection_set](assetId:///29c63a74-4db4-4068-bd57-9fb519b0c598)|Delete a collection set.|  
|[sp_syscollector_update_collection_set](assetId:///2dccc3cd-0e93-4e3e-a4e5-8fe89b31bd63)|Change a collection set configuration.|  
|[sp_syscollector_upload_collection_set](assetId:///eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc)|Upload collection set data to the management data warehouse. This is effectively an on-demand upload.|  
  
 **Working with collection items**  
  
 The following table describes the stored procedures that you can use to work with collection items.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collection_item](assetId:///60dacf13-ca12-4844-b417-0bc0a8bf0ddb)|Create a collection item.|  
|[sp_syscollector_delete_collection_item](assetId:///9c2b0990-1d3d-4a59-94a0-3cca6fef4681)|Delete a collection item.|  
|[sp_syscollector_update_collection_item](assetId:///7a0d36c8-c6e9-431d-a5a4-6c1802bce846)|Update a collection item.|  
  
 **Working with collector types**  
  
 The following table describes the stored procedures that you can use to work with collector types.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_create_collector_type](assetId:///568e9119-b9b0-4284-9cef-3878c691de5f)|Create a collector type.|  
|[sp_syscollector_update_collector_type (Transact-SQL)](assetId:///3c414dfd-d9ca-4320-81aa-949465b967bf)|Update a collector type.|  
|[sp_syscollector_delete_collector_type](assetId:///3f32905e-0005-42cb-aef1-7bd04c51fbac)|Delete a collector type.|  
  
 **Getting configuration information**  
  
 The following table describes the views that you can use for getting configuration information and execution log data.  
  
|View name|Description|  
|---------------|-----------------|  
|[syscollector_config_store](assetId:///f15f6b05-6808-4b76-b6a8-48dec844cf63)|Get data collector configuration.|  
|[syscollector_collection_items](assetId:///a279ecd1-a59c-4315-9f08-bf221f00a465)|Get collection item information.|  
|[syscollector_collection_sets](assetId:///db0def92-f25b-45da-9709-eab972b33800)|Get collection set information.|  
|[syscollector_collector_types](assetId:///d5cd30bb-89fd-4814-a7e8-9074f043f90f)|Get collector type information.|  
|[syscollector_execution_log](assetId:///11554d64-0426-42ce-b7ce-5591f67864d2)|Get information about collection set and package execution.|  
|[syscollector_execution_stats](assetId:///23e35ac5-fbbf-4922-970c-f4fac44c1263)|Get information about task execution.|  
|[syscollector_execution_log_full](assetId:///6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b)|Get information when the execution log is full.|  
  
 **Configuring access to the management data warehouse**  
  
 The following table describes the stored procedures that you can use to configure access to the management data warehouse.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_warehouse_database_name](assetId:///a85aca1b-8135-4c81-9a05-da5aec76f1ed)|Specify the database name defined in the connection string for the management data warehouse.|  
|[sp_syscollector_set_warehouse_instance_name](assetId:///5320fcd4-bed1-468f-b784-a5e10fcfaeb6)|Specify the instance defined in the connection string for the management data warehouse.|  
  
 **Configuring the management data warehouse**  
  
 The following table describes the stored procedures that you can use to work with the management data warehouse configuration.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[core.sp_create_snapshot](assetId:///ff297bda-0ee2-4fda-91c8-7000377775e3)|Create a collection snapshot in the management data warehouse.|  
|[core.sp_update_data_source](assetId:///66b95f96-6df7-4657-9b3c-86a58c788ca5)|Update the data source for data collection.|  
|[core.sp_add_collector_type](assetId:///1d981037-2147-464e-a456-7d8e479bce89)|Add a collector type to the management data warehouse.|  
|[core.sp_remove_collector_type](assetId:///88ceba25-e41a-405f-a416-bb68918a0024)|Remove a collector type from the management data warehouse.|  
|[core.sp_purge_data](assetId:///056076c3-8adf-4f51-8a1b-ca39696ac390)|Delete data from the management data warehouse.|  
  
 **Working with upload packages**  
  
 The following table describes the stored procedures that you can use to work with upload packages.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_set_cache_window](assetId:///660f2749-392f-46bf-89f3-27764d848507)|Configure the number of data upload retries.|  
|[sp_syscollector_set_cache_directory](assetId:///df56d5a5-8961-494f-a745-d752ca63805a)|Specify temporary storage for data between upload retries.|  
  
 **Working with the data collection execution log**  
  
 The following table describes the stored procedures that you can use to work with the data collection execution log.  
  
|Procedure name|Description|  
|--------------------|-----------------|  
|[sp_syscollector_delete_execution_log_tree](assetId:///0a9a7c5b-c3cc-40ca-b524-e948a8cce4e4)|Delete collection set entries from the execution log.|  
  
### Functions  
 The following table describes the functions that you can use to obtain execution and trace information.  
  
|Function name|Description|  
|-------------------|-----------------|  
|[fn_syscollector_get_execution_details](assetId:///d59ddf0c-72c0-4c57-bc83-aef260e4e105)|Get [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] execution log data for a specific package.|  
|[fn_syscollector_get_execution_stats](assetId:///793ad72c-a992-4a8d-8584-bcb6b3b476f1)|Get execution statistics for a collection set or package. This information includes errors that are logged.|  
|[snapshots.fn_trace_getdata](assetId:///ac28ef48-f4f4-4bf2-ba22-d44e1be88172)|Get the events that are logged when the Generic SQL Trace collector type is used to collect data.|  
  
## See Also  
 [Execute a Stored Procedure](../../Topics/TopicNameContainA/Execute-a-Stored-Procedure.md)   
 [Introducing SQL Server Management Studio](assetId:///f289e978-14ca-46ef-9e61-e1fe5fd593be)   
 [Data Collection](../../Topics/TopicNameNotContainA/Data-Collection.md)