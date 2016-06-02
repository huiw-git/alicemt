---
title: Restore the master Database (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
---
# Restore the master Database (Transact-SQL)
  This topic explains how to restore the **master** database from a full database backup.  
  
### To restore the master database  
  
1.  Start the server instance in single\-user mode.  
  
     For information about how to specify the single\-user startup parameter \(**\-m**\), see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20Server%20Startup%20Options%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
2.  To restore a full database backup of **master**, use the following [RESTORE DATABASE](../Topic/RESTORE%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement:  
  
     `RESTORE DATABASE master FROM`  *\<backup\_device\>*  `WITH REPLACE`  
  
     The REPLACE option instructs [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to restore the specified database even when a database of the same name already exists. The existing database, if any, is deleted. In single\-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md). For more information, see [Use the sqlcmd Utility](../../Topics\TopicNameNotContainA/Use-the-sqlcmd-Utility.md).  
  
    > [!IMPORTANT]  
    >  After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] shuts down and terminates the **sqlcmd** process. Before you restart the server instance, remove the single\-user startup parameter. For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20Server%20Startup%20Options%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
3.  Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.  
  
## Example  
 The following example restores the `master` database on the default server instance. The example assumes that the server instance is already running in single\-user mode. The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  For a named instance, the **sqlcmd** command must specify the **\-S***\<ComputerName\>*\\*\<InstanceName\>* option.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## See Also  
 [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md)   
 [Troubleshoot Orphaned Users &#40;SQL Server&#41;](../Topic/Troubleshoot%20Orphaned%20Users%20\(SQL%20Server\).md)   
 [Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md)   
 [Rebuild System Databases](../../Topics\TopicNameNotContainA/Rebuild-System-Databases.md)   
 [Database Engine Service Startup Options](../../Topics\TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)   
 [SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Start SQL Server in Single-User Mode](../../Topics\TopicNameNotContainA/Start-SQL-Server-in-Single-User-Mode.md)  
  
  