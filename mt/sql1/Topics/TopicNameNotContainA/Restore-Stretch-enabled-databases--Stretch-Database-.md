---
title: Restore Stretch-enabled databases (Stretch Database)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cebc1f6d-d5ea-460d-ae60-d047d29c2723
---
# Restore Stretch-enabled databases (Stretch Database)
  Restore a backed up database when necessary to recover from many types of failures, errors, and disasters.
  
  For more info about backup, see [Backup Stretch-enabled databases](../../Topics/TopicNameNotContainA/Backup-Stretch-enabled-databases--Stretch-Database-.md).

> [!TIP] Backup is only one part of a complete high availability and business continuity solution. For more info about high availability, see [High Availability Solutions](../../Topics/TopicNameNotContainA/High-Availability-Solutions--SQL-Server-.md).

## Restore your SQL Server data
To recover from hardware failure or corruption, restore the Stretch-enabled SQL Server database from a backup. You can continue to use the SQL Server restore methods that you currently use. For more info, see [Restore and Recovery Overview](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md).

After you restore the SQL Server database, you have to run the stored procedure **sys.sp_rda_reauthorize_db** to re-establish the connection between the Stretch-enabled SQL Server database and the remote Azure database. For more info, see [Restore the connection between the SQL Server database and the remote Azure database](#reconnect).

## Restore your remote Azure data

### Recover a live Azure database
The SQL Server Stretch Database service on Azure snapshots all live data at least every 8 hours using Azure Storage Snapshots. These snapshots are maintained for 7 days. This allows you to restore the data to one of at least 21 points in time within the past 7 days up to the time when the last snapshot was taken.

To restore a live Azure database to an earlier point in time by using the Azure portal, do the following things.

1. Log in to the [Azure portal][].
2. On the left side of the screen select **BROWSE** and then select **SQL Databases**.
3. Navigate to your database and select it.
4. At the top of the database blade, click **Restore**.
5. Specify a new **Database name**, select a **Restore Point** and then click **Create**.
6. The database restore process will begin and can be monitored using **NOTIFICATIONS**.

### Recover a deleted Azure database
The SQL Server Stretch Database service on Azure takes a database snapshot before a database is dropped and retains it for 7 days. After this occurs, it no longer retains snapshots from the live database. This lets you restore a deleted database to the point when it was deleted.

To restore a deleted Azure database to the point when it was deletedby using the Azure portal, do the following things.

1. Log in to the [Azure portal][].
2. On the left side of the screen select **BROWSE** and then select **SQL Servers**.
3. Navigate to your server and select it.
4. Scroll down to Operations on your server's blade, click the **Deleted Databases** tile.
5. Select the deleted database you want to restore.
5. Specify a new **Database name** and click **Create**.
6. The database restore process will begin and can be monitored using **NOTIFICATIONS**.

### Recover an Azure database in a different Azure region  
The SQL Server Stretch Database service on Azure copies snapshots asynchronously to a different geographical Azure region for added recoverability in case of a regional failure. If you cannot access your database because of a failure in an Azure region, you can restore your database to one of the geo-redundant snapshots.

> [!NOTE] Recovering the Azure database in a different Azure region requires changing the connection string in client applications after recovery and may result in permanent data loss. Do this type of recovery only when the outage is likely to last a long time. 

To recover an Azure database to an earlier point in time in a different Azure region by using the Azure portal, do the following things.

1. Log in to the [Azure portal][]
2. On the left side of the screen select **+NEW**, then select **Data and Storage**, and then select **SQL Data Warehouse**
3. Select **BACKUP** as the source and then select the geo-redundant backup you want to recover from
4. Specify the rest of the database properties and click **Create**
5. The database restore process will begin and can be monitored using **NOTIFICATIONS**

After you restore the Azure database in a different region, you have to run the stored procedures **sys.sp_rda_deauthorize_db** and **sys.sp_rda_reauthorize_db** to re-establish the connection between the Stretch-enabled SQL Server database and the remote Azure database. For more info, see [Restore the connection between the SQL Server database and the remote Azure database](#reconnect).

## <a name="reconnect"></a>Restore the connection between the SQL Server database and the remote Azure database

1.  If you're going to connect to a restored Azure database with a different name or in a different region, run the stored procedure [sys.sp_rda_deauthorize_db](sys.sp_rda_deauthorize_db%20\(Transact-SQL\).md) to disconnect from the previous Azure database.  
  
2.  Run the stored procedure [sys.sp_rda_reauthorize_db](../Topic/sys.sp_rda_reauthorize_db%20\(Transact-SQL\).md) to reconnect the local Stretch-enabled database to the Azure database.  
  
    -   Provide the existing database scoped credential as a sysname or a varchar(128) value. (Don't use varchar(max).) You can look up the credential name in the view **sys.database_scoped_credentials**.  
  
    -   Specify whether to make a copy of the remote data and connect to the copy (recommended).  
  
    ```tsql  
    DECLARE @credentialName nvarchar(128);   
    SET @credentialName = N'<existing_database_scoped_credential_name>';   
    EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
    ```  
    
  ## See Also  
 [Backup Stretch-enabled databases](../../Topics/TopicNameNotContainA/Backup-Stretch-enabled-databases--Stretch-Database-.md)  
 [Manage and troubleshoot Stretch Database](../../Topics/TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)   
 [sys.sp_rda_reauthorize_db](../Topic/sys.sp_rda_reauthorize_db%20\(Transact-SQL\).md) 
 [sys.sp_rda_deauthorize_db](sys.sp_rda_deauthorize_db%20\(Transact-SQL\).md)  
 [Back Up and Restore of SQL Server Databases](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)  
 
 [Azure portal]: https://portal.azure.com/
 