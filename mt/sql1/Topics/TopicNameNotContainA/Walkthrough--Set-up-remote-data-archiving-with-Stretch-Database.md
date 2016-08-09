---
title: "Walkthrough: Set up remote data archiving with Stretch Database"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75f9f17e-352a-48a1-8691-e1148b9b0944
caps.latest.revision: 15
manager: jhubbard
robots: noindex,nofollow
---
# Walkthrough: Set up remote data archiving with Stretch Database
Follow these steps to enable Stretch Database and migrate historical data to Azure SQL Database.  
  
## Typical workflow to enable Stretch Database  
  
### Get an Azure account  
 Stretch Database migrates data to an Azure SQL Database. Therefore you have to have an Azure account and a subscription for billing. To get an Azure account, [click here](http://azure.microsoft.com/en-us/pricing/free-trial/).  
  
### Enable Stretch for the local server  
 Before you can enable Stretch for a database or a table, you have to enable it on the local server. To enable Stretch on the server, run **sp_configure** and turn on the **remote data archive** option, as shown in the following example.  
  
```  
EXEC sp_configure 'remote data archive' , '1';  
RECONFIGURE;  
  
```  
  
 Running **sp_configure** to set the value of the **remote data archive** option requires sysadmin or serveradmin permissions.  
  
### Identify databases and tables that are eligible for Stretch  
 Download SQL Server 2016 Upgrade Advisor from [here](http://go.microsoft.com/fwlink/?LinkID=613421) and run it. Run the Stretch Database Advisor to identify databases and tables that are good candidates for Stretch Database. For more info, see [Identify databases and tables for Stretch Database by running Stretch Database Advisor](../../Topics/TopicNameNotContainA/Identify-databases-and-tables-for-Stretch-Database-by-running-Stretch-Database-Advisor.md).  
  
### Enable Stretch for a database  
 Enable Stretch for a database as a prerequisite to enable Stretch for individual tables.  
  
 Enabling Stretch for a database or a table requires db_owner permissions. Enabling Stretch for a database also requires CONTROL DATABASE permissions.  
  
##### Enable Stretch for a database by using SQL Server Management Studio  
  
1.  In SQL Server Management Studio, in Object Explorer, select the database for which you want to enable Stretch.  
  
2.  Right-click and select **Tasks**, and then select **Enable Database for Stretch**.  
  
3.  On the **Microsoft Azure Sign-in** page of the wizard, sign in to your Azure account and select the subscription to use for billing.  
  
4.  On the **Stretch Settings** page of the wizard, do the following things to configure the Azure SQL Database server.  
  
    1.  Select an Azure location for the server.  
  
    2.  Create the credential for the server.  
  
    3.  Configure a firewall rule to allow connections to the server.  
  
5.  On the **Summary** page of the wizard, review your choices and then click **Finish**.  
  
### Enable Stretch for a table  
 Enable Stretch for a table to start migrating historical data to Azure SQL Database.  
  
 Enabling Stretch for a database or a table requires db_owner permissions. Enabling Stretch for a table also requires ALTER permissions on the table.  
  
##### Enable Stretch for a table by using SQL Server Management Studio  
  
1.  In SQL Server Management Studio, in Object Explorer, select the table for which you want to enable Stretch.  
  
2.  Right-click and select **Enable Stretch**.  
  
## Optional tasks  
  
### Pause and resume data migration  
 Pause data migration on individual tables to troubleshoot problems on the local server or to maximize the available network bandwidth.  
  
##### Pause data migration by using SQL Server Management Studio  
  
1.  In SQL Server Management Studio, in Object Explorer, select the Stretch-enabled table for which you want to pause data migration.  
  
2.  Right-click and select **Pause Stretch**.  
  
##### Resume data migration by using SQL Server Management Studio  
  
1.  In SQL Server Management Studio, in Object Explorer, select the Stretch-enabled table for which you want to resume data migration.  
  
2.  Right-click and select **Resume Stretch**.  
  
### Check the status of data migration  
 Open the dynamic management view **sys.dm_db_rda_migration_status** to see how many batches and rows of data have been migrated. For more info, see [sys.dm_db_rda_migration_status (Transact-SQL)](assetId:///faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd). There is no visual indicator for the status of migration.  
  
### Backup and restore a Stretch-enabled database  
 You can continue to back up and restore Stretch-enabled databases by using the methods that you currently use. After you restore a backup of a Stretch-enabled database, run the stored procedure [sys.sp_reauthorize_remote_data_archive (Transact-SQL)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd) to reconnect the local Stretch-enabled database to the remote SQL Database.  
  
### Find info about local Stretch-enabled databases and tables  
 Open the catalog views **sys.databases** and **sys.tables** to see info about the local Stretch-enabled databases and tables. For more info, see [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) and [sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090).  
  
### Find info about remote databases and tables  
 Open the catalog views **sys.remote_data_archive_databases** and **sys.remote_data_archive_tables** to see info about the remote SQL Databases and tables in which archived data is stored. For more info, see [sys.remote_data_archive_databases (Transact-SQL)](assetId:///25bffb0c-9821-40b4-88cf-75f854891a09) and [sys.remote_data_archive_tables (Transact-SQL)](assetId:///765069b7-60fd-414c-875f-3455460b75cd).