---
title: Resource Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
---
# Resource Database
  The Resource database is a read\-only database that contains all the system objects that are included with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system objects, such as sys.objects, are physically persisted in the Resource database, but they logically appear in the sys schema of every database. The Resource database does not contain user data or user metadata.  
  
 The Resource database makes upgrading to a new version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] an easier and faster procedure. In earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], upgrading required dropping and creating system objects. Because the Resource database file contains all system objects, an upgrade is now accomplished simply by copying the single Resource database file to the local server.  
  
## Physical Properties of Resource  
 The physical file names of the Resource database are mssqlsystemresource.mdf and mssqlsystemresource.ldf. These files are located in \<*drive*\>:\\Program Files\\Microsoft SQL Server\\MSSQL\<version\>.\<*instance\_name*\>\\MSSQL\\Binn\\ and should not be moved. Each instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has one and only one associated mssqlsystemresource.mdf file, and instances do not share this file.  
  
> [!WARNING]  
>  Upgrades and service packs sometimes provide a new resource database which is installed to the BINN folder. Changing the location of the resource database is not supported or recommended.  
  
## Backing Up and Restoring the Resource Database  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot back up the Resource database. You can perform your own file\-based or a disk\-based backup by treating the mssqlsystemresource.mdf file as if it were a binary \(.EXE\) file, rather than a database file, but you cannot use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to restore your backups. Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current Resource database with an out\-of\-date or potentially insecure version.  
  
> [!IMPORTANT]  
>  After restoring a backup of mssqlsystemresource.mdf, you must reapply any subsequent updates.  
  
## Accessing the Resource Database  
 The Resource database should only be modified by or at the direction of a Microsoft Customer Support Services \(CSS\) specialist. The ID of the Resource database is always 32767. Other important values associated with the Resource database are the version number and the last time that the database was updated.  
  
 **To determine the version number of the** Resource **database, use**:  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 **To determine when the** Resource **database was last updated, use**:  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 **To access SQL definitions of system objects, use the OBJECT\_DEFINITION function:**  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## Related Content  
 [System Databases](../../Topics\TopicNameNotContainA/System-Databases.md)  
  
 [Diagnostic Connection for Database Administrators](../../Topics\TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)  
  
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../Topic/OBJECT_DEFINITION%20\(Transact-SQL\).md)  
  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)  
  
 [Start SQL Server in Single-User Mode](../../Topics\TopicNameNotContainA/Start-SQL-Server-in-Single-User-Mode.md)  
  
  