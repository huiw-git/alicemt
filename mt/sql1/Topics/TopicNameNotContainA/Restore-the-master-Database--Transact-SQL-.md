---
title: "Restore the master Database (Transact-SQL)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
caps.latest.revision: 42
caps.handback.revision: 0
manager: jhubbard
---
# Restore the master Database (Transact-SQL)
This topic explains how to restore the **master** database from a full database backup.  
  
### To restore the master database  
  
1.  Start the server instance in single-user mode.  
  
     For information about how to specify the single-user startup parameter (**-m**), see [Configure Server Startup Options (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Server-Startup-Options--SQL-Server-Configuration-Manager-.md).  
  
2.  To restore a full database backup of **master**, use the following [RESTORE DATABASE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)[!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement:  
  
     `RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`  
  
     The REPLACE option instructs [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to restore the specified database even when a database of the same name already exists. The existing database, if any, is deleted. In single-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../Topics/TopicNameNotContainA/sqlcmd-Utility.md). For more information, see [Use the sqlcmd Utility](../../Topics/TopicNameNotContainA/Use-the-sqlcmd-Utility.md).  
  
    > [!IMPORTANT]  
    >  After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] shuts down and terminates the **sqlcmd** process. Before you restart the server instance, remove the single-user startup parameter. For more information, see [Configure Server Startup Options (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Server-Startup-Options--SQL-Server-Configuration-Manager-.md).  
  
3.  Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.  
  
## Example  
 The following example restores the `master` database on the default server instance. The example assumes that the server instance is already running in single-user mode. The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  For a named instance, the **sqlcmd** command must specify the **-S***<ComputerName\>*\\*<InstanceName\>* option.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## See Also  
 [Complete Database Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Simple-Recovery-Model-.md)   
 [Complete Database Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Full-Recovery-Model-.md)   
 [Troubleshoot Orphaned Users (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Orphaned-Users--SQL-Server-.md)   
 [Database Detach and Attach (SQL Server)](../../Topics/TopicNameNotContainA/Database-Detach-and-Attach--SQL-Server-.md)   
 [Rebuild System Databases](../../Topics/TopicNameNotContainA/Rebuild-System-Databases.md)   
 [Database Engine Service Startup Options](../../Topics/TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)   
 [SQL Server Configuration Manager](../../Topics/TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Back Up and Restore of System Databases (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-System-Databases--SQL-Server-.md)   
 [RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)   
 [Start SQL Server in Single-User Mode](../../Topics/TopicNameNotContainA/Start-SQL-Server-in-Single-User-Mode.md)