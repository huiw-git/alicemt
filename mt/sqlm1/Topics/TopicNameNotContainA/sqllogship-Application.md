---
title: sqllogship Application
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ae70041-f3d9-46e4-8fa8-31088572a9f8
---
# sqllogship Application
  The **sqllogship** application performs a backup, copy, or restore operation and associated clean\-up tasks for a log shipping configuration. The operation is performed on a specific instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for a specific database.  
  
 ![Topic link icon](../../Images\Image\ImageNotContaina/Topic_Link.gif "Topic_Link") For the syntax conventions, see [Command Prompt Utility Reference &#40;Database Engine&#41;](../Topic/Command%20Prompt%20Utility%20Reference%20\(Database%20Engine\).md).  
  
## Syntax  
  
```  
  
sqllogship -server instance_name { -backup primary_id | -copy secondary_id | -restore secondary_id } [ –verboselevel level ] [ –logintimeout timeout_value ] [ -querytimeout timeout_value ]  
```  
  
## Arguments  
 **\-server** *instance\_name*  
 Specifies the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] where the operation will run. The server instance to specify depends on which log\-shipping operation is being specified. For **\-backup**, *instance\_name* must be the name of the primary server in a log shipping configuration. For **\-copy** or **\-restore**, *instance\_name* must be the name of a secondary server in a log shipping configuration.  
  
 **\-backup** *primary\_id*  
 Performs a backup operation for the primary database whose primary ID is specified by *primary\_id*. You can obtain this ID by selecting it from the [log\_shipping\_primary\_databases](../Topic/log_shipping_primary_databases%20\(Transact-SQL\).md) system table or by using the [sp\_help\_log\_shipping\_primary\_database](../Topic/sp_help_log_shipping_primary_database%20\(Transact-SQL\).md) stored procedure.  
  
 The backup operation creates the log backup in the backup directory. The **sqllogship** application then cleans out any old backup files, based on the file retention period. Next, the application logs history for the backup operation on the primary server and the monitor server. Finally, the application runs [sp\_cleanup\_log\_shipping\_history](../Topic/sp_cleanup_log_shipping_history%20\(Transact-SQL\).md), which cleans out old history information, based on the retention period.  
  
 **\-copy** *secondary\_id*  
 Performs a copy operation to copy backups from the specified secondary server for the secondary database, or databases, whose secondary ID is specified by *secondary\_id*. You can obtain this ID by selecting it from the [log\_shipping\_secondary](../Topic/log_shipping_secondary%20\(Transact-SQL\).md) system table or by using the [sp\_help\_log\_shipping\_secondary\_database](../Topic/sp_help_log_shipping_secondary_database%20\(Transact-SQL\).md) stored procedure.  
  
 The operation copies the backup files from the backup directory to the destination directory. The **sqllogship** application then logs the history for the copy operation on the secondary server and the monitor server.  
  
 **\-restore** *secondary\_id*  
 Performs a restore operation on the specified secondary server for the secondary database, or databases, whose secondary ID is specified by *secondary\_id*. You can obtain this ID by using the **sp\_help\_log\_shipping\_secondary\_database** stored procedure.  
  
 Any backup files in the destination directory that were created after the most recent restore point are restored to the secondary database, or databases. The **sqllogship** application then cleans out any old backup files, based on the file retention period. Next, the application logs history for the restore operation on the secondary server and the monitor server. Finally, the application runs **sp\_cleanup\_log\_shipping\_history**, which cleans out old history information, based on the retention period.  
  
 **–verboselevel** *level*  
 Specifies the level of messages added to the log shipping history. *level* is one of the following integers:  
  
|Level|Description|  
|-----------|-----------------|  
|0|Output no tracing and debugging messages.|  
|1|Output error\-handling messages.|  
|2|Output warnings and error\-handling messages.|  
|**3**|Output informational messages, warnings, and error\-handling messages. This is the default value.|  
|4|Output all debugging and tracing messages.|  
  
 **–logintimeout** *timeout\_value*  
 Specifies the amount of time allotted for attempting to log in to the server instance before the attempt times out. The default is 15 seconds. *timeout\_value* is **int***.*  
  
 **\-querytimeout** *timeout\_value*  
 Specifies the amount of time allotted for starting the specified operation before the attempt times out. The default is no timeout period. *timeout\_value* is **int***.*  
  
## Remarks  
 We recommend that you use the backup, copy, and restore jobs to perform the backup, copy and restore when possible. To start these jobs from a batch operation or other application, call the [sp\_start\_job](../Topic/sp_start_job%20\(Transact-SQL\).md) stored procedure.  
  
 The log shipping history created by **sqllogship** is interspersed with the history created by log shipping backup, copy, and restore jobs. If you plan to use **sqllogship** repeatedly to perform backup, copy, or restore operations for a log shipping configuration, consider disabling the corresponding log shipping job or jobs. For more information, see [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md).  
  
 The **sqllogship** application, SqlLogShip.exe, is installed in the x:\\Program Files\\Microsoft SQL Server\\130\\Tools\\Binn directory.  
  
## Permissions  
 **sqllogship** uses Windows Authentication. The Windows Authentication account where the command is run requires Windows directory access and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] permissions. The requirement depends on whether the **sqllogship** command specifies the **\-backup**, **\-copy**, or **\-restore** option.  
  
|Option|Directory access|Permissions|  
|------------|----------------------|-----------------|  
|**\-backup**|Requires read\/write access to the backup directory.|Requires the same permissions as the BACKUP statement. For more information, see [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md).|  
|**\-copy**|Requires read access to the backup directory and write access to the copy directory.|Requires the same permissions as the [sp\_help\_log\_shipping\_secondary\_database](../Topic/sp_help_log_shipping_secondary_database%20\(Transact-SQL\).md) stored procedure.|  
|**\-restore**|Requires read\/write access to the copy directory.|Requires the same permissions as the RESTORE statement. For more information, see [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md).|  
  
> [!NOTE]  
>  To find out the paths of the backup and copy directories, you can run the **sp\_help\_log\_shipping\_secondary\_database** stored procedure or view the **log\_shipping\_secondary** table in **msdb**. The paths of the backup directory and destination directory are in the **backup\_source\_directory** and **backup\_destination\_directory** columns, respectively.  
  
## See Also  
 [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](../Topic/log_shipping_primary_databases%20\(Transact-SQL\).md)   
 [log_shipping_secondary &#40;Transact-SQL&#41;](../Topic/log_shipping_secondary%20\(Transact-SQL\).md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../Topic/sp_cleanup_log_shipping_history%20\(Transact-SQL\).md)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](../Topic/sp_help_log_shipping_primary_database%20\(Transact-SQL\).md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../Topic/sp_help_log_shipping_secondary_database%20\(Transact-SQL\).md)   
 [sp_start_job &#40;Transact-SQL&#41;](../Topic/sp_start_job%20\(Transact-SQL\).md)  
  
  