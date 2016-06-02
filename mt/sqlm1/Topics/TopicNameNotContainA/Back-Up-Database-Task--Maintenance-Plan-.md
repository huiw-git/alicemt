---
title: Back Up Database Task (Maintenance Plan)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed1ef012-fa14-4ba5-bafe-d1527ba065b3
---
# Back Up Database Task (Maintenance Plan)
  Use the **Back Up Database Task** dialog to add a backup task to the maintenance plan. Backing up the database is important in case of system or hardware failure \(or user errors\) that cause the database to be damaged in some way, thus requiring a backed\-up copy to be restored. This task allows you to perform full, differential, files and filegroups, and transaction log backups.  
  
 **To create a backup database task**  
  
-   [Create a Maintenance Plan](../../Topics\TopicNameContainA/Create-a-Maintenance-Plan.md)  
  
## Options  
 **Connection**  
 Select the server connection to use when performing this task.  
  
 **New**  
 Create a new server connection to use when performing this task. The **New Connection** dialog box is described below.  
  
 **Databases**  
 Specify the databases affected by this task. When selected, the drop down list provides the following options: **All databases**, **All system databases**, **All user databases**, **These specific databases**.  
  
 **All databases**  
 Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases.  
  
 **All system databases \(master, msdb, model\)**  
 Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system databases. No maintenance tasks are run against user\-created databases.  
  
 **All user databases \(excluding master, model, msdb, tempdb\)**  
 Generate a maintenance plan that runs maintenance tasks against all user\-created databases. No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system databases.  
  
 **These databases**  
 Generate a maintenance plan that runs maintenance tasks against only those databases that are selected. At least one database in the list must be selected if this option is chosen.  
  
 **Backup type**  
 Shows the type of backup to be performed.  
  
 **Backup component**  
 Select **Database** to back up the entire database. Select **File and filegroups** to back up only a portion of the database. If selected, provide the file or filegroup name. When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**. To perform file or filegroup backups, create a task for each database.  
  
 **Backup set will expire**  
 Specify when the backup set can be overwritten by another backup set.  
  
 **Back up to**  
 Back up the database to a file or to tape. Only tape devices attached to the computer containing the database are available.  
  
 **Back up databases across one or more files**  
 Click **Add** to open the **Select Backup Destination** dialog box, and provide one or more a disk location, or tape device.  
  
 **If backup files exist**  
 Select **Append** to add this backup to the end of the file. Select **Overwrite**, to remove any old backup in the file and replace them with this new backup.  
  
 **Create a backup file for every database**  
 Create a backup file in the location specified in the folder box. One file will be created for each database selected.  
  
 **Create a sub\-directory for each database**  
 Select to place each database in a subfolder.  
  
> [!IMPORTANT]  
>  Although maintenance plans can create subdirectories, maintenance tasks cannot delete subdirectories. This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.  
  
> [!IMPORTANT]  
>  The subdirectory inherits permissions from the parent directory. Restrict permissions to avoid unauthorized access.  
  
 **Folder**  
 Specify the folder to contain the automatically created database files.  
  
 **Backup file extension**  
 Specify the extension to use for the backup files. The default is **.bak**.  
  
 **Verify backup integrity**  
 Verify that the backup set is complete and that all volumes are readable.  
  
 **Back up the tail of the log, and leave the database in the restoring state**  
 Perform a log backup as the last step before restoring a database. For more information, see [Tail-Log Backups &#40;SQL Server&#41;](../Topic/Tail-Log%20Backups%20\(SQL%20Server\).md).  
  
 **Set backup compression**  
 In [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] \(or a later version\), select one the following [backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md) values:  
  
|||  
|-|-|  
|**Use the default server setting**|Click to use the server\-level default.<br /><br /> This default is set by the **backup compression default** server\-configuration option. For information about how to view the current setting of this option,  see [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md).|  
|**Compress backup**|Click to compress the backup, regardless of the server\-level default.<br /><br /> **\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations. Therefore, you might want to create low\-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md). For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../Topic/Use%20Resource%20Governor%20to%20Limit%20CPU%20Usage%20by%20Backup%20Compression%20\(Transact-SQL\).md).|  
|**Do not compress backup**|Click to create an uncompressed backup, regardless of the server\-level default.|  
  
 **View T\-SQL**  
 View the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements performed against the server for this task, based on the selected options.  
  
> [!NOTE]  
>  When the number of objects affected is large, this display can take a considerable amount of time.  
  
## New Connection Dialog Box  
 **Connection name**  
 Enter a name for the new connection.  
  
 **Select or enter a server name**  
 Select a server to connect to when performing this task.  
  
 **Refresh**  
 Refresh the list of available servers.  
  
 **Enter information to log on to the server**  
 Specify how to authenticate against the server.  
  
 **Use Windows integrated security**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] with Windows Authentication.  
  
 **Use a specific user name and password**  
 Connect to an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication. This option is not available.  
  
 **User name**  
 Provide a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login to use when authenticating. This option is not available.  
  
 **Password**  
 Provide a password to use when authenticating. This option is not available.  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)  
  
  