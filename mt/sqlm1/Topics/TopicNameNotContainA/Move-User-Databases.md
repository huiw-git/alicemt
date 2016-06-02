---
title: Move User Databases
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad9a4e92-13fb-457d-996a-66ffc2d55b79
---
# Move User Databases
  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can move the data, log, and full\-text catalog files of a user database to a new location by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md) statement. This method applies to moving database files within the same instance [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. To move a database to another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or to another server, use [backup and restore](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md) or [detach and attach operations](../Topic/Move%20a%20Database%20Using%20Detach%20and%20Attach%20\(Transact-SQL\).md).  
  
## Considerations  
 When you move a database onto another server instance, to provide a consistent experience to users and applications, you might have to re\-create some or all the metadata for the database. For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md).  
  
 Some features of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] change the way that the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] stores information in the database files. These features are restricted to specific editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. A database that contains these features cannot be moved to an edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that does not support them. Use the sys.dm\_db\_persisted\_sku\_features dynamic management view to list all edition\-specific features that are enabled in the current database.  
  
 The procedures in this topic require the logical name of the database files. To obtain the name, query the name column in the [sys.master\_files](../Topic/sys.master_files%20\(Transact-SQL\).md) catalog view.  
  
 Starting with [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], full\-text catalogs are integrated into the database rather than being stored in the file system. The full\-text catalogs now move automatically when you move a database.  
  
## Planned Relocation Procedure  
 To move a data or log file as part of a planned relocation, follow these steps:  
  
1.  Run the following statement.  
  
    ```  
    ALTER DATABASE database_name SET OFFLINE;  
    ```  
  
2.  Move the file or files to the new location.  
  
3.  For each file moved, run the following statement.  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name, FILENAME = 'new_path\os_file_name' );  
    ```  
  
4.  Run the following statement.  
  
    ```  
    ALTER DATABASE database_name SET ONLINE;  
    ```  
  
5.  Verify the file change by running the following query.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## Relocation for Scheduled Disk Maintenance  
 To relocate a file as part of a scheduled disk maintenance process, follow these steps:  
  
1.  For each file to be moved, run the following statement.  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
2.  Stop the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or shut down the system to perform maintenance. For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md).  
  
3.  Move the file or files to the new location.  
  
4.  Restart the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or the server. For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)  
  
5.  Verify the file change by running the following query.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## Failure Recovery Procedure  
 If a file must be moved because of a hardware failure, use the following steps to relocate the file to a new location.  
  
> [!IMPORTANT]  
>  If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.  
  
1.  Stop the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] if it is started.  
  
2.  Start the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in master\-only recovery mode by entering one of the following commands at the command prompt.  
  
    -   For the default \(MSSQLSERVER\) instance, run the following command.  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   For a named instance, run the following command.  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md).  
  
3.  For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to run the following statement.  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
     For more information about how to use the **sqlcmd** utility, see [Use the sqlcmd Utility](../../Topics\TopicNameNotContainA/Use-the-sqlcmd-Utility.md).  
  
4.  Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
5.  Stop the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
6.  Move the file or files to the new location.  
  
7.  Start the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For example, run: `NET START MSSQLSERVER`.  
  
8.  Verify the file change by running the following query.  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## Examples  
 The following example moves the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] log file to a new location as part of a planned relocation.  
  
```  
USE master;  
GO  
-- Return the logical file name.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
GO  
ALTER DATABASE AdventureWorks2012 SET OFFLINE;  
GO  
-- Physically move the file to a new location.  
-- In the following statement, modify the path specified in FILENAME to  
-- the new location of the file on your server.  
ALTER DATABASE AdventureWorks2012   
    MODIFY FILE ( NAME = AdventureWorks2012_Log,   
                  FILENAME = 'C:\NewLoc\AdventureWorks2012_Log.ldf');  
GO  
ALTER DATABASE AdventureWorks2012 SET ONLINE;  
GO  
--Verify the new location.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
```  
  
## See Also  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md)   
 [Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md)   
 [Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md)   
 [Move Database Files](../../Topics\TopicNameNotContainA/Move-Database-Files.md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)  
  
  