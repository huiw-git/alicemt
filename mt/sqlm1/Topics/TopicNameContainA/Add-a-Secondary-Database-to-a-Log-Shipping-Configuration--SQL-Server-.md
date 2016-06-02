---
title: Add a Secondary Database to a Log Shipping Configuration (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
---
# Add a Secondary Database to a Log Shipping Configuration (SQL Server)
  This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To add a log shipping secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The log\-shipping stored procedures require membership in the **sysadmin** fixed server role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To add a log shipping secondary database  
  
1.  Right\-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.  
  
2.  Under **Select a page**, click **Transaction Log Shipping**.  
  
3.  Under **Secondary server instances and databases**, click **Add**.  
  
4.  Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that you want to use as your secondary server.  
  
5.  In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.  
  
6.  On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.  
  
7.  On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied. This folder is often located on the secondary server.  
  
8.  Note the copy schedule listed in the **Schedule** box under **Copy job**. If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent schedule as needed. This schedule should approximate the backup schedule.  
  
9. On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.  
  
10. If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.  
  
11. If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.  
  
12. Choose an alert threshold under **Alert if no restore occurs within**.  
  
13. Note the restore schedule listed in the **Schedule** box under **Restore job**. If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent schedule as needed. This schedule should approximate the backup schedule.  
  
14. Click **OK**.  
  
15. Click **OK** on the Database Properties dialog box to begin the configuration process.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To add a log shipping secondary database  
  
1.  On the secondary server, execute [sp\_add\_log\_shipping\_secondary\_primary](../Topic/sp_add_log_shipping_secondary_primary%20\(Transact-SQL\).md) supplying the details of the primary server and database. This stored procedure returns the secondary ID and the copy and restore job IDs.  
  
2.  On the secondary server, execute [sp\_add\_jobschedule](../Topic/sp_add_jobschedule%20\(Transact-SQL\).md) to set the schedule for the copy and restore jobs.  
  
3.  On the secondary server, execute [sp\_add\_log\_shipping\_secondary\_database](../Topic/sp_add_log_shipping_secondary_database%20\(Transact-SQL\).md) to add a secondary database.  
  
4.  On the primary server, execute [sp\_add\_log\_shipping\_primary\_secondary](../Topic/sp_add_log_shipping_primary_secondary%20\(Transact-SQL\).md) to add the required information about the new secondary database to the primary server.  
  
5.  On the secondary server, enable the copy and restore jobs. For more information, see [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Upgrading Log Shipping to SQL Server 2016 &#40;Transact-SQL&#41;](../Topic/Upgrading%20Log%20Shipping%20to%20SQL%20Server%202016%20\(Transact-SQL\).md)  
  
-   [Configure Log Shipping &#40;SQL Server&#41;](../Topic/Configure%20Log%20Shipping%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20a%20Log%20Shipping%20Configuration%20\(SQL%20Server\).md)  
  
-   [Remove Log Shipping &#40;SQL Server&#41;](../Topic/Remove%20Log%20Shipping%20\(SQL%20Server\).md)  
  
-   [View the Log Shipping Report &#40;SQL Server Management Studio&#41;](../Topic/View%20the%20Log%20Shipping%20Report%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Monitor Log Shipping &#40;Transact-SQL&#41;](../Topic/Monitor%20Log%20Shipping%20\(Transact-SQL\).md)  
  
-   [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](../Topic/Fail%20Over%20to%20a%20Log%20Shipping%20Secondary%20\(SQL%20Server\).md)  
  
## See Also  
 [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md)   
 [Log Shipping Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)  
  
  