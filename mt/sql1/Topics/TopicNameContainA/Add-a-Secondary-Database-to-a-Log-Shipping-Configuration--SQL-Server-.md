---
title: "Add a Secondary Database to a Log Shipping Configuration (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Add a Secondary Database to a Log Shipping Configuration (SQL Server)
This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To add a log shipping secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The log-shipping stored procedures require membership in the **sysadmin** fixed server role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To add a log shipping secondary database  
  
1.  Right-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.  
  
2.  Under **Select a page**, click **Transaction Log Shipping**.  
  
3.  Under **Secondary server instances and databases**, click **Add**.  
  
4.  Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that you want to use as your secondary server.  
  
5.  In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.  
  
6.  On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.  
  
7.  On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied. This folder is often located on the secondary server.  
  
8.  Note the copy schedule listed in the **Schedule** box under **Copy job**. If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent schedule as needed. This schedule should approximate the backup schedule.  
  
9. On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.  
  
10. If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.  
  
11. If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.  
  
12. Choose an alert threshold under **Alert if no restore occurs within**.  
  
13. Note the restore schedule listed in the **Schedule** box under **Restore job**. If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent schedule as needed. This schedule should approximate the backup schedule.  
  
14. Click **OK**.  
  
15. Click **OK** on the Database Properties dialog box to begin the configuration process.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To add a log shipping secondary database  
  
1.  On the secondary server, execute [sp_add_log_shipping_secondary_primary](assetId:///bfbbbee2-c255-4a59-a963-47d6e980a8e2) supplying the details of the primary server and database. This stored procedure returns the secondary ID and the copy and restore job IDs.  
  
2.  On the secondary server, execute [sp_add_jobschedule](assetId:///ffce19d9-d1d6-45b4-89fd-ad0f60822ba0) to set the schedule for the copy and restore jobs.  
  
3.  On the secondary server, execute [sp_add_log_shipping_secondary_database](assetId:///d29e1c24-3a3c-47a4-a726-4584afa6038a) to add a secondary database.  
  
4.  On the primary server, execute [sp_add_log_shipping_primary_secondary](assetId:///23b3e100-5318-410e-b8f3-51c89b2dd777) to add the required information about the new secondary database to the primary server.  
  
5.  On the secondary server, enable the copy and restore jobs. For more information, see [Disable or Enable a Job](assetId:///5041261f-0c32-4d4a-8bee-59a6c16200dd).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Upgrading Log Shipping to SQL Server 2016 (Transact-SQL)](../../Topics/TopicNameNotContainA/Upgrading-Log-Shipping-to-SQL-Server-2016--Transact-SQL-.md)  
  
-   [Configure Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Log-Shipping--SQL-Server-.md)  
  
-   [Remove a Secondary Database from a Log Shipping Configuration (SQL Server)](../../Topics/TopicNameContainA/Remove-a-Secondary-Database-from-a-Log-Shipping-Configuration--SQL-Server-.md)  
  
-   [Remove Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/Remove-Log-Shipping--SQL-Server-.md)  
  
-   [View the Log Shipping Report (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-the-Log-Shipping-Report--SQL-Server-Management-Studio-.md)  
  
-   [Monitor Log Shipping (Transact-SQL)](../../Topics/TopicNameNotContainA/Monitor-Log-Shipping--Transact-SQL-.md)  
  
-   [Fail Over to a Log Shipping Secondary (SQL Server)](../../Topics/TopicNameContainA/Fail-Over-to-a-Log-Shipping-Secondary--SQL-Server-.md)  
  
## See Also  
 [About Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)   
 [Log Shipping Tables and Stored Procedures](../../Topics/TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)