---
title: Stretch 12 backup
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2ee9ec2-2dc4-4caf-8346-75b8a8dbaa09
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Stretch 12 backup
  To back up and restore Stretch\-enabled databases, you can continue to use  the methods that you currently use. For more info about [!INCLUDE[ssNoVersion](../Token/ssNoVersion_md.md)] backup and restore, see [Back Up and Restore of SQL Server Databases](assetId:///570a21b3-ad29-44a9-aa70-deb2fbd34f27).

 A backup of a Stretch\-enabled database is a shallow backup that does not include the data migrated to the remote server.

 Stretch Database provides full support for point in time restore. After you restore your SQL Server database to a point in time and reauthorize the connection to Azure, Stretch Database reconciles the remote data to the same point in time. For more info about point in time restore in SQL Server, see [Restore a SQL Server Database to a Point in Time \(Full Recovery Model\)](assetId:///3a5daefd-08a8-4565-b54f-28ad01a47d32). For info about the stored procedure that you have to run after a restore to reauthorize the connection to Azure, see [sys.sp\_rda\_reauthorize\_db \(Transact\-SQL\)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd).

##  <a name="Reconnect"></a> Restore a Stretch\-enabled database from a backup

1.  Restore the database from a backup.

2.  Create a database master key for the Stretch\-enabled database. For more info, see [CREATE MASTER KEY \(Transact\-SQL\)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76)

3.  Create a database scoped credential for the Stretch\-enabled database. For more info, see [CREATE DATABASE SCOPED CREDENTIAL \(Transact\-SQL\)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).

4.  Run the stored procedure [sys.sp\_rda\_reauthorize\_db \(Transact\-SQL\)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd) to reconnect the local Stretch\-enabled database to Azure. Provide the database scoped credential created in a previous step as a sysname or a varchar\(128\) value. \(Don't use varchar\(max\).\)

    ```tsql
    Declare @credentialName nvarchar(128); 
    SET @credentialName = N’<database_scoped_credential_name_created_previously>’; 
    EXEC sp_rda_reauthorize_db @credentialName;

    ```

##  <a name="MoreInfo"></a> More info about backup and restore
 Backups on a database with Stretch Database enabled contain only local data and eligible data at the point in time when the backup runs. These backups also contain information about the remote endpoint where the database’s remote data resides. This is known as a "shallow backup". Deep backups that contain all data in the database, both local and remote, are not supported in [!INCLUDE[ssSQL15]()].

 ![](c6a383e8-72ac-4e55-b9e5-61b7790bed9d)

 When you restore a backup of a database with Stretch Database enabled, this operation restores the local data and eligible data to the database as expected. \(Eligible data is data that has not yet been moved, but will be moved to Azure based on the Stretch Database configuration of the tables.\) After the restore operation runs, the database contains local and eligible data from the point when the backup ran, but it does not have the required credentials and artifacts to connect to the remote endpoint.

 ![](376db23b-0d30-4ec4-a72e-7bc1c872ef56)

 You have to run the stored procedure **sys.sp\_rda\_reauthorize\_db** to re\-establish the connection between the local database and its remote endpoint. Only a db\_owner can perform this operation. This stored procedure also requires the remote endpoint’s administrator user name and password. \(In [!INCLUDE[ssSQL15]()], this means that you have to provide the administrator login and password for the target Azure server\).

 ![](6225340f-6bb2-4603-9d03-14444d35b9ad)

 After you re\-establish the connection, Stretch Database attempts to reconcile eligible data in the local database with remote data by creating a copy of the remote data on the remote endpoint and linking it with the local database. This process is automatic and requires no user intervention. After this reconciliation runs, the local database and the remote endpoint are in a consistent state.

 ![](3563eb97-1ded-4222-9c45-197e7fe0fcb5)

## See Also
 [Manage and troubleshoot Stretch Database](assetId:///6334db3e-9297-44df-8d53-211187a95520) 
 [sys.sp\_rda\_reauthorize\_db \(Transact\-SQL\)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd) 
 [Back Up and Restore of SQL Server Databases](assetId:///570a21b3-ad29-44a9-aa70-deb2fbd34f27)

  