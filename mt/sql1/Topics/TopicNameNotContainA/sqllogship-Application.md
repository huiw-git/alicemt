---
title: "sqllogship Application"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ae70041-f3d9-46e4-8fa8-31088572a9f8
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# sqllogship Application
The **sqllogship** application performs a backup, copy, or restore operation and associated clean-up tasks for a log shipping configuration. The operation is performed on a specific instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for a specific database.  
  
 ![Topic link icon](../../Topics/TopicNameNotContainA/images/Topic_Link.gif "Topic_Link") For the syntax conventions, see [Command Prompt Utility Reference (Database Engine)](../../Topics/TopicNameNotContainA/Command-Prompt-Utility-Reference--Database-Engine-.md).  
  
## Syntax  
  
```  
  
sqllogship -server instance_name { -backup primary_id | -copy secondary_id | -restore secondary_id } [ –verboselevel level ] [ –logintimeout timeout_value ] [ -querytimeout timeout_value ]  
```  
  
## Arguments  
 **-server** *instance_name*  
 Specifies the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] where the operation will run. The server instance to specify depends on which log-shipping operation is being specified. For **-backup**, *instance_name* must be the name of the primary server in a log shipping configuration. For **-copy** or **-restore**, *instance_name* must be the name of a secondary server in a log shipping configuration.  
  
 **-backup** *primary_id*  
 Performs a backup operation for the primary database whose primary ID is specified by *primary_id*. You can obtain this ID by selecting it from the [log_shipping_primary_databases](assetId:///56888756-a798-42be-9b5e-0f9aa05a2cc6) system table or by using the [sp_help_log_shipping_primary_database](assetId:///e711b01c-ef29-4eb6-a016-0e647e337818) stored procedure.  
  
 The backup operation creates the log backup in the backup directory. The **sqllogship** application then cleans out any old backup files, based on the file retention period. Next, the application logs history for the backup operation on the primary server and the monitor server. Finally, the application runs [sp_cleanup_log_shipping_history](assetId:///96d236a9-1d0e-4f83-a4d3-f825b7381e46), which cleans out old history information, based on the retention period.  
  
 **-copy** *secondary_id*  
 Performs a copy operation to copy backups from the specified secondary server for the secondary database, or databases, whose secondary ID is specified by *secondary_id*. You can obtain this ID by selecting it from the [log_shipping_secondary](assetId:///69723419-4544-49c6-a517-adb30ffa5741) system table or by using the [sp_help_log_shipping_secondary_database](assetId:///11ce42ca-d3f1-44c8-9cac-214ca8896b9a) stored procedure.  
  
 The operation copies the backup files from the backup directory to the destination directory. The **sqllogship** application then logs the history for the copy operation on the secondary server and the monitor server.  
  
 **-restore** *secondary_id*  
 Performs a restore operation on the specified secondary server for the secondary database, or databases, whose secondary ID is specified by *secondary_id*. You can obtain this ID by using the **sp_help_log_shipping_secondary_database** stored procedure.  
  
 Any backup files in the destination directory that were created after the most recent restore point are restored to the secondary database, or databases. The **sqllogship** application then cleans out any old backup files, based on the file retention period. Next, the application logs history for the restore operation on the secondary server and the monitor server. Finally, the application runs **sp_cleanup_log_shipping_history**, which cleans out old history information, based on the retention period.  
  
 **–verboselevel** *level*  
 Specifies the level of messages added to the log shipping history. *level* is one of the following integers:  
  
|Level|Description|  
|-----------|-----------------|  
|0|Output no tracing and debugging messages.|  
|1|Output error-handling messages.|  
|2|Output warnings and error-handling messages.|  
|**3**|Output informational messages, warnings, and error-handling messages. This is the default value.|  
|4|Output all debugging and tracing messages.|  
  
 **–logintimeout** *timeout_value*  
 Specifies the amount of time allotted for attempting to log in to the server instance before the attempt times out. The default is 15 seconds. *timeout_value* is **int***.*  
  
 **-querytimeout** *timeout_value*  
 Specifies the amount of time allotted for starting the specified operation before the attempt times out. The default is no timeout period. *timeout_value* is **int***.*  
  
## Remarks  
 We recommend that you use the backup, copy, and restore jobs to perform the backup, copy and restore when possible. To start these jobs from a batch operation or other application, call the [sp_start_job](assetId:///8a91df6a-eb84-4512-9a17-4a6e32a9538a) stored procedure.  
  
 The log shipping history created by **sqllogship** is interspersed with the history created by log shipping backup, copy, and restore jobs. If you plan to use **sqllogship** repeatedly to perform backup, copy, or restore operations for a log shipping configuration, consider disabling the corresponding log shipping job or jobs. For more information, see [How to: Disable a Job (SQL Server Management Studio)](assetId:///5041261f-0c32-4d4a-8bee-59a6c16200dd).  
  
 The **sqllogship** application, SqlLogShip.exe, is installed in the x:\Program Files\Microsoft SQL Server\130\Tools\Binn directory.  
  
## Permissions  
 **sqllogship** uses Windows Authentication. The Windows Authentication account where the command is run requires Windows directory access and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] permissions. The requirement depends on whether the **sqllogship** command specifies the **-backup**, **-copy**, or **-restore** option.  
  
|Option|Directory access|Permissions|  
|------------|----------------------|-----------------|  
|**-backup**|Requires read/write access to the backup directory.|Requires the same permissions as the BACKUP statement. For more information, see [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1).|  
|**-copy**|Requires read access to the backup directory and write access to the copy directory.|Requires the same permissions as the [sp_help_log_shipping_secondary_database](assetId:///11ce42ca-d3f1-44c8-9cac-214ca8896b9a) stored procedure.|  
|**-restore**|Requires read/write access to the copy directory.|Requires the same permissions as the RESTORE statement. For more information, see [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1).|  
  
> [!NOTE]  
>  To find out the paths of the backup and copy directories, you can run the **sp_help_log_shipping_secondary_database** stored procedure or view the **log_shipping_secondary** table in **msdb**. The paths of the backup directory and destination directory are in the **backup_source_directory** and **backup_destination_directory** columns, respectively.  
  
## See Also  
 [About Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)   
 [log_shipping_primary_databases (Transact-SQL)](assetId:///56888756-a798-42be-9b5e-0f9aa05a2cc6)   
 [log_shipping_secondary (Transact-SQL)](assetId:///69723419-4544-49c6-a517-adb30ffa5741)   
 [sp_cleanup_log_shipping_history (Transact-SQL)](assetId:///96d236a9-1d0e-4f83-a4d3-f825b7381e46)   
 [sp_help_log_shipping_primary_database (Transact-SQL)](assetId:///e711b01c-ef29-4eb6-a016-0e647e337818)   
 [sp_help_log_shipping_secondary_database (Transact-SQL)](assetId:///11ce42ca-d3f1-44c8-9cac-214ca8896b9a)   
 [sp_start_job (Transact-SQL)](assetId:///8a91df6a-eb84-4512-9a17-4a6e32a9538a)