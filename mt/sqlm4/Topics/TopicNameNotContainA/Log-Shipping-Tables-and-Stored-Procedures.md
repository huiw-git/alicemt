---
title: Log Shipping Tables and Stored Procedures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
---
# Log Shipping Tables and Stored Procedures
  This topic describes all of the tables and stored procedures associated with a log shipping configuration. All log shipping tables are stored in **msdb** on each server. The tables below describe which tables and stored procedures are used on which servers in a log shipping configuration.  
  
## Primary Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log\_shipping\_monitor\_alert](../Topic/log_shipping_monitor_alert%20\(Transact-SQL\).md)|Stores alert job ID. This table is only used on the primary server if a remote monitor server has not been configured.|  
|[log\_shipping\_monitor\_error\_detail](../Topic/log_shipping_monitor_error_detail%20\(Transact-SQL\).md)|Stores error detail for log shipping jobs associated with this primary server.|  
|[log\_shipping\_monitor\_history\_detail](../Topic/log_shipping_monitor_history_detail%20\(Transact-SQL\).md)|Stores history detail for log shipping jobs associated with this primary server.|  
|[log\_shipping\_monitor\_primary](../Topic/log_shipping_monitor_primary%20\(Transact-SQL\).md)|Stores one monitor record for this primary database.|  
|[log\_shipping\_primary\_databases](../Topic/log_shipping_primary_databases%20\(Transact-SQL\).md)|Contains configuration information for primary databases on a given server. Stores one row per primary database.|  
|[log\_shipping\_primary\_secondaries](../Topic/log_shipping_primary_secondaries%20\(Transact-SQL\).md)|Maps primary databases to secondary databases.|  
  
## Primary Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp\_add\_log\_shipping\_primary\_database](../Topic/sp_add_log_shipping_primary_database%20\(Transact-SQL\).md)|Sets up the primary database for a log shipping configuration, including the backup job, local monitor record, and remote monitor record.|  
|[sp\_add\_log\_shipping\_primary\_secondary](../Topic/sp_add_log_shipping_primary_secondary%20\(Transact-SQL\).md)|Adds a secondary database name to an existing primary database.|  
|[sp\_change\_log\_shipping\_primary\_database](../Topic/sp_change_log_shipping_primary_database%20\(Transact-SQL\).md)|Changes primary database settings including local and remote monitor record.|  
|[sp\_cleanup\_log\_shipping\_history](../Topic/sp_cleanup_log_shipping_history%20\(Transact-SQL\).md)|Cleans up history locally and on the monitor based on retention period.|  
|[sp\_delete\_log\_shipping\_primary\_database](../Topic/sp_delete_log_shipping_primary_database%20\(Transact-SQL\).md)|Removes log shipping of primary database including backup job as well as local and remote history.|  
|[sp\_delete\_log\_shipping\_primary\_secondary](../Topic/sp_delete_log_shipping_primary_secondary%20\(Transact-SQL\).md)|Removes a secondary database name from a primary database.|  
|[sp\_help\_log\_shipping\_primary\_database](../Topic/sp_help_log_shipping_primary_database%20\(Transact-SQL\).md)|Retrieves primary database settings and displays the values from the **log\_shipping\_primary\_databases** and **log\_shipping\_monitor\_primary** tables.|  
|[sp\_help\_log\_shipping\_primary\_secondary](../Topic/sp_help_log_shipping_primary_secondary%20\(Transact-SQL\).md)|Retrieves secondary database names for a primary database.|  
|[sp\_refresh\_log\_shipping\_monitor](../Topic/sp_refresh_log_shipping_monitor%20\(Transact-SQL\).md)|Refreshes the monitor with the latest information for the specified log shipping agent.|  
  
## Secondary Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log\_shipping\_monitor\_alert](../Topic/log_shipping_monitor_alert%20\(Transact-SQL\).md)|Stores alert job ID. This table is only used on the secondary server if a remote monitor server has not been configured.|  
|[log\_shipping\_monitor\_error\_detail](../Topic/log_shipping_monitor_error_detail%20\(Transact-SQL\).md)|Stores error detail for log shipping jobs associated with this secondary server.|  
|[log\_shipping\_monitor\_history\_detail](../Topic/log_shipping_monitor_history_detail%20\(Transact-SQL\).md)|Stores history detail for log shipping jobs associated with this secondary server.|  
|[log\_shipping\_monitor\_secondary](../Topic/log_shipping_monitor_secondary%20\(Transact-SQL\).md)|Stores one monitor record per secondary database associated with this secondary server.|  
|[log\_shipping\_secondary](../Topic/log_shipping_secondary%20\(Transact-SQL\).md)|Contains configuration information for the secondary databases on a given server. Stores one row per secondary ID.|  
|[log\_shipping\_secondary\_databases](../Topic/log_shipping_secondary_databases%20\(Transact-SQL\).md)|Stores configuration information for a given secondary database. Stores one row per secondary database.|  
  
> [!NOTE]  
>  Secondary databases on the same secondary server for a given primary database share the settings in the **log\_shipping\_secondary** table. If a shared setting is altered for one secondary database, the setting is altered for all of them.  
  
## Secondary Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp\_add\_log\_shipping\_secondary\_database](../Topic/sp_add_log_shipping_secondary_database%20\(Transact-SQL\).md)|Sets up a secondary database for log shipping.|  
|[sp\_add\_log\_shipping\_secondary\_primary](../Topic/sp_add_log_shipping_secondary_primary%20\(Transact-SQL\).md)|Sets up the primary information, adds local and remote monitor links, and creates copy and restore jobs on the secondary server for the specified primary database.|  
|[sp\_change\_log\_shipping\_secondary\_database](../Topic/sp_change_log_shipping_secondary_database%20\(Transact-SQL\).md)|Changes secondary database settings including local and remote monitor records.|  
|[sp\_change\_log\_shipping\_secondary\_primary](../Topic/sp_change_log_shipping_secondary_primary%20\(Transact-SQL\).md)|Changes secondary database settings such as source and destination directory, and file retention period.|  
|[sp\_cleanup\_log\_shipping\_history](../Topic/sp_cleanup_log_shipping_history%20\(Transact-SQL\).md)|Cleans up history locally and on the monitor based on retention period.|  
|[sp\_delete\_log\_shipping\_secondary\_database](../Topic/sp_delete_log_shipping_secondary_database%20\(Transact-SQL\).md)|Removes a secondary database and the local history and remote history.|  
|[sp\_delete\_log\_shipping\_secondary\_primary](../Topic/sp_delete_log_shipping_secondary_primary%20\(Transact-SQL\).md)|Removes the information about the specified primary server from the secondary server.|  
|[sp\_help\_log\_shipping\_secondary\_database](../Topic/sp_help_log_shipping_secondary_database%20\(Transact-SQL\).md)|Retrieves secondary database settings from the **log\_shipping\_secondary**, **log\_shipping\_secondary\_databases**, and **log\_shipping\_monitor\_secondary** tables.|  
|[sp\_help\_log\_shipping\_secondary\_primary](../Topic/sp_help_log_shipping_secondary_primary%20\(Transact-SQL\).md)|This stored procedure retrieves the settings for a given primary database on the secondary server.|  
|[sp\_refresh\_log\_shipping\_monitor](../Topic/sp_refresh_log_shipping_monitor%20\(Transact-SQL\).md)|Refreshes the monitor with the latest information for the specified log shipping agent.|  
  
## Monitor Server Tables  
  
|Table|Description|  
|-----------|-----------------|  
|[log\_shipping\_monitor\_alert](../Topic/log_shipping_monitor_alert%20\(Transact-SQL\).md)|Stores alert job ID.|  
|[log\_shipping\_monitor\_error\_detail](../Topic/log_shipping_monitor_error_detail%20\(Transact-SQL\).md)|Stores error detail for log shipping jobs.|  
|[log\_shipping\_monitor\_history\_detail](../Topic/log_shipping_monitor_history_detail%20\(Transact-SQL\).md)|Stores history detail for log shipping jobs.|  
|[log\_shipping\_monitor\_primary](../Topic/log_shipping_monitor_primary%20\(Transact-SQL\).md)|Stores one monitor record per primary database associated with this monitor server.|  
|[log\_shipping\_monitor\_secondary](../Topic/log_shipping_monitor_secondary%20\(Transact-SQL\).md)|Stores one monitor record per secondary database associated with this monitor server.|  
  
## Monitor Server Stored Procedures  
  
|Stored Procedure|Description|  
|----------------------|-----------------|  
|[sp\_add\_log\_shipping\_alert\_job](../Topic/sp_add_log_shipping_alert_job%20\(Transact-SQL\).md)|Creates a log shipping alert job if one has not already been created.|  
|[sp\_delete\_log\_shipping\_alert\_job](../Topic/sp_delete_log_shipping_alert_job%20\(Transact-SQL\).md)|Removes a log shipping alert job if there are no associated primary databases.|  
|[sp\_help\_log\_shipping\_alert\_job](../Topic/sp_help_log_shipping_alert_job%20\(Transact-SQL\).md)|Returns the job ID of the alert job.|  
|[sp\_help\_log\_shipping\_monitor\_primary](../Topic/sp_help_log_shipping_monitor_primary%20\(Transact-SQL\).md)|Returns monitor records for the specified primary database from the **log\_shipping\_monitor\_primary** table.|  
|[sp\_help\_log\_shipping\_monitor\_secondary](../Topic/sp_help_log_shipping_monitor_secondary%20\(Transact-SQL\).md)|Returns monitor records for the specified secondary database from the **log\_shipping\_monitor\_secondary** table.|  
  
  