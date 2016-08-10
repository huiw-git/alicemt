---
title: "Backup Stretch-enabled databases (Stretch Database)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18f0dff0-d8ce-4bee-a935-76ed6dfb3208
caps.latest.revision: 39
manager: jhubbard
---
# Backup Stretch-enabled databases (Stretch Database)
To back up and restore Stretch-enabled databases, you can continue to use  the methods that you currently use. For more info about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] backup and restore, see [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md).  
  
 A backup of a Stretch-enabled database is a shallow backup that does not include the data migrated to the remote server.  
  
 Stretch Database provides full support for point in time restore. After you restore your SQL Server database to a point in time and reauthorize the connection to Azure, Stretch Database reconciles the remote data to the same point in time. For more info about point in time restore in SQL Server, see [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md). For info about the stored procedure that you have to run after a restore to reauthorize the connection to Azure, see [sys.sp_rda_reauthorize_db (Transact-SQL)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd).  
  
##  <a name="Reconnect"></a> Restore a Stretch-enabled database from a backup  
  
1.  Restore the database from a backup.  
  
2.  Run the stored procedure [sys.sp_rda_reauthorize_db (Transact-SQL)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd) to reconnect the local Stretch-enabled database to Azure.  
  
    -   Provide the existing database scoped credential as a sysname or a varchar(128) value. (Don't use varchar(max).) You can look up the credential name in the view **sys.database_scoped_credentials**.  
  
    -   Specify whether to make a copy of the remote data and connect to the copy.  
  
    ```tsql  
    DECLARE @credentialName nvarchar(128);   
    SET @credentialName = N'<existing_database_scoped_credential_name>';   
    EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 0;  
  
    ```  
  
##  <a name="MoreInfo"></a> More info about backup and restore  
 Backups on a database with Stretch Database enabled contain only local data and eligible data at the point in time when the backup runs. These backups also contain information about the remote endpoint where the database’s remote data resides. This is known as a "shallow backup". Deep backups that contain all data in the database, both local and remote, are not supported in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)].  
  
 When you restore a backup of a database with Stretch Database enabled, this operation restores the local data and eligible data to the database as expected. (Eligible data is data that has not yet been moved, but will be moved to Azure based on the Stretch Database configuration of the tables.) After the restore operation runs, the database contains local and eligible data from the point when the backup ran, but it does not have the required credentials and artifacts to connect to the remote endpoint.  
  
 You have to run the stored procedure **sys.sp_rda_reauthorize_db** to re-establish the connection between the local database and its remote endpoint. Only a db_owner can perform this operation. This stored procedure also requires the administrator login and password for the target Azure server).  
  
 After you re-establish the connection, Stretch Database attempts to reconcile eligible data in the local database with remote data by creating a copy of the remote data on the remote endpoint and linking it with the local database. This process is automatic and requires no user intervention. After this reconciliation runs, the local database and the remote endpoint are in a consistent state.  
  
## See Also  
 [Manage and troubleshoot Stretch Database](../../Topics/TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)   
 [sys.sp_rda_reauthorize_db (Transact-SQL)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd)   
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)