---
title: "Log Shipping Tables and Stored Procedures"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
caps.latest.revision: 21
manager: jhubbard
---
# Log Shipping Tables and Stored Procedures
This topic describes all of the tables and stored procedures associated with a log shipping configuration. All log shipping tables are stored in **msdb** on each server. The tables below describe which tables and stored procedures are used on which servers in a log shipping configuration.  
  
## Primary Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](assetId:///1c775e48-9898-4149-b9d1-04d465f23438)|Stores alert job ID. This table is only used on the primary server if a remote monitor server has not been configured.|  
|[log_shipping_monitor_error_detail](assetId:///0c38a625-60d2-4ee2-bcf3-2ba367914220)|Stores error detail for log shipping jobs associated with this primary server.|  
|[log_shipping_monitor_history_detail](assetId:///7080c888-323b-4206-a1ab-e6c51f9e2579)|Stores history detail for log shipping jobs associated with this primary server.|  
|[log_shipping_monitor_primary](assetId:///5f629a29-1a62-40e6-ae33-6f6b7dd09a36)|Stores one monitor record for this primary database.|  
|[log_shipping_primary_databases](assetId:///56888756-a798-42be-9b5e-0f9aa05a2cc6)|Contains configuration information for primary databases on a given server. Stores one row per primary database.|  
|[log_shipping_primary_secondaries](assetId:///4b315c70-7265-4acd-b35b-a4dbb7881d98)|Maps primary databases to secondary databases.|  
  
## Primary Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_primary_database](assetId:///69531611-113f-46b5-81a6-7bf496d0353c)|Sets up the primary database for a log shipping configuration, including the backup job, local monitor record, and remote monitor record.|  
|[sp_add_log_shipping_primary_secondary](assetId:///23b3e100-5318-410e-b8f3-51c89b2dd777)|Adds a secondary database name to an existing primary database.|  
|[sp_change_log_shipping_primary_database](assetId:///8c9dce6b-d2a3-4ca7-a832-8f59a5adb214)|Changes primary database settings including local and remote monitor record.|  
|[sp_cleanup_log_shipping_history](assetId:///96d236a9-1d0e-4f83-a4d3-f825b7381e46)|Cleans up history locally and on the monitor based on retention period.|  
|[sp_delete_log_shipping_primary_database](assetId:///cb1d5d00-2805-4d47-bd04-545232067345)|Removes log shipping of primary database including backup job as well as local and remote history.|  
|[sp_delete_log_shipping_primary_secondary](assetId:///d6f71a12-f7b1-4a1c-9639-a533b8287b0c)|Removes a secondary database name from a primary database.|  
|[sp_help_log_shipping_primary_database](assetId:///e711b01c-ef29-4eb6-a016-0e647e337818)|Retrieves primary database settings and displays the values from the **log_shipping_primary_databases** and **log_shipping_monitor_primary** tables.|  
|[sp_help_log_shipping_primary_secondary](assetId:///bc0044b4-7831-4ff9-8856-825c76aa9893)|Retrieves secondary database names for a primary database.|  
|[sp_refresh_log_shipping_monitor](assetId:///edefb912-31c5-4d99-9aba-06629afd0171)|Refreshes the monitor with the latest information for the specified log shipping agent.|  
  
## Secondary Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](assetId:///1c775e48-9898-4149-b9d1-04d465f23438)|Stores alert job ID. This table is only used on the secondary server if a remote monitor server has not been configured.|  
|[log_shipping_monitor_error_detail](assetId:///0c38a625-60d2-4ee2-bcf3-2ba367914220)|Stores error detail for log shipping jobs associated with this secondary server.|  
|[log_shipping_monitor_history_detail](assetId:///7080c888-323b-4206-a1ab-e6c51f9e2579)|Stores history detail for log shipping jobs associated with this secondary server.|  
|[log_shipping_monitor_secondary](assetId:///afbe1bb7-89a7-4020-9408-0af64a043c2e)|Stores one monitor record per secondary database associated with this secondary server.|  
|[log_shipping_secondary](assetId:///69723419-4544-49c6-a517-adb30ffa5741)|Contains configuration information for the secondary databases on a given server. Stores one row per secondary ID.|  
|[log_shipping_secondary_databases](assetId:///ba2374af-86b8-480c-a10c-51e7c4e3ae23)|Stores configuration information for a given secondary database. Stores one row per secondary database.|  
  
> [!NOTE]  
>  Secondary databases on the same secondary server for a given primary database share the settings in the **log_shipping_secondary** table. If a shared setting is altered for one secondary database, the setting is altered for all of them.  
  
## Secondary Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_secondary_database](assetId:///d29e1c24-3a3c-47a4-a726-4584afa6038a)|Sets up a secondary database for log shipping.|  
|[sp_add_log_shipping_secondary_primary](assetId:///bfbbbee2-c255-4a59-a963-47d6e980a8e2)|Sets up the primary information, adds local and remote monitor links, and creates copy and restore jobs on the secondary server for the specified primary database.|  
|[sp_change_log_shipping_secondary_database](assetId:///3ebcf2f1-980f-4543-a84b-fbaeea54eeac)|Changes secondary database settings including local and remote monitor records.|  
|[sp_change_log_shipping_secondary_primary](assetId:///5bcb4df7-6df3-4f2b-9207-b97b5addf2a6)|Changes secondary database settings such as source and destination directory, and file retention period.|  
|[sp_cleanup_log_shipping_history](assetId:///96d236a9-1d0e-4f83-a4d3-f825b7381e46)|Cleans up history locally and on the monitor based on retention period.|  
|[sp_delete_log_shipping_secondary_database](assetId:///c71b21c0-ec04-4fbd-9735-01128b736935)|Removes a secondary database and the local history and remote history.|  
|[sp_delete_log_shipping_secondary_primary](assetId:///507fc744-73d9-4cb7-8d2a-bcff88841c6a)|Removes the information about the specified primary server from the secondary server.|  
|[sp_help_log_shipping_secondary_database](assetId:///11ce42ca-d3f1-44c8-9cac-214ca8896b9a)|Retrieves secondary database settings from the **log_shipping_secondary**, **log_shipping_secondary_databases**, and **log_shipping_monitor_secondary** tables.|  
|[sp_help_log_shipping_secondary_primary](assetId:///1310fdaf-edb5-4294-9739-7fb37c2c2cb5)|This stored procedure retrieves the settings for a given primary database on the secondary server.|  
|[sp_refresh_log_shipping_monitor](assetId:///edefb912-31c5-4d99-9aba-06629afd0171)|Refreshes the monitor with the latest information for the specified log shipping agent.|  
  
## Monitor Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](assetId:///1c775e48-9898-4149-b9d1-04d465f23438)|Stores alert job ID.|  
|[log_shipping_monitor_error_detail](assetId:///0c38a625-60d2-4ee2-bcf3-2ba367914220)|Stores error detail for log shipping jobs.|  
|[log_shipping_monitor_history_detail](assetId:///7080c888-323b-4206-a1ab-e6c51f9e2579)|Stores history detail for log shipping jobs.|  
|[log_shipping_monitor_primary](assetId:///5f629a29-1a62-40e6-ae33-6f6b7dd09a36)|Stores one monitor record per primary database associated with this monitor server.|  
|[log_shipping_monitor_secondary](assetId:///afbe1bb7-89a7-4020-9408-0af64a043c2e)|Stores one monitor record per secondary database associated with this monitor server.|  
  
## Monitor Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_alert_job](assetId:///dd95d96e-8963-4aa9-bdcc-3e4b1bc002d3)|Creates a log shipping alert job if one has not already been created.|  
|[sp_delete_log_shipping_alert_job](assetId:///5d6c7f07-a163-48fa-8c1f-abc252043dde)|Removes a log shipping alert job if there are no associated primary databases.|  
|[sp_help_log_shipping_alert_job](assetId:///4d4b4577-c393-4961-b2d3-b56e980b787b)|Returns the job ID of the alert job.|  
|[sp_help_log_shipping_monitor_primary](assetId:///d9dfcb8f-1da6-49ca-a2c8-411574915434)|Returns monitor records for the specified primary database from the **log_shipping_monitor_primary** table.|  
|[sp_help_log_shipping_monitor_secondary](assetId:///3ac091ea-c9a8-4c05-a0b6-1ccf4e001339)|Returns monitor records for the specified secondary database from the **log_shipping_monitor_secondary** table.|