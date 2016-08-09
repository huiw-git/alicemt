---
title: "Remove a Secondary Database from a Log Shipping Configuration (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Remove a Secondary Database from a Log Shipping Configuration (SQL Server)
This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To remove a log shipping secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The log-shipping stored procedures require membership in the **sysadmin** fixed server role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove a log shipping secondary database  
  
1.  Connect to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is currently the log shipping primary server and expand that instance.  
  
2.  Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.  
  
3.  Under **Select a page**, click **Transaction Log Shipping**.  
  
4.  Under **Secondary server instances and databases**, click the database you want to remove.  
  
5.  Click **Remove**.  
  
6.  Click **OK** to update the configuration.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To Remove a Secondary Database  
  
1.  On the primary server, execute [sp_delete_log_shipping_primary_secondary](assetId:///d6f71a12-f7b1-4a1c-9639-a533b8287b0c) to delete the information about the secondary database from the primary server.  
  
2.  On the secondary server, execute [sp_delete_log_shipping_secondary_database](assetId:///c71b21c0-ec04-4fbd-9735-01128b736935) to delete the secondary database.  
  
    > [!NOTE]  
    >  If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.  
  
3.  On the secondary server, disable the copy and restore jobs. For more information, see [Disable or Enable a Job](assetId:///5041261f-0c32-4d4a-8bee-59a6c16200dd).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Upgrading Log Shipping to SQL Server 2016 (Transact-SQL)](../../Topics/TopicNameNotContainA/Upgrading-Log-Shipping-to-SQL-Server-2016--Transact-SQL-.md)  
  
-   [Configure Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/Configure-Log-Shipping--SQL-Server-.md)  
  
-   [Add a Secondary Database to a Log Shipping Configuration (SQL Server)](../../Topics/TopicNameContainA/Add-a-Secondary-Database-to-a-Log-Shipping-Configuration--SQL-Server-.md)  
  
-   [Remove Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/Remove-Log-Shipping--SQL-Server-.md)  
  
-   [View the Log Shipping Report (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/View-the-Log-Shipping-Report--SQL-Server-Management-Studio-.md)  
  
-   [Monitor Log Shipping (Transact-SQL)](../../Topics/TopicNameNotContainA/Monitor-Log-Shipping--Transact-SQL-.md)  
  
-   [Fail Over to a Log Shipping Secondary (SQL Server)](../../Topics/TopicNameContainA/Fail-Over-to-a-Log-Shipping-Secondary--SQL-Server-.md)  
  
## See Also  
 [About Log Shipping (SQL Server)](../../Topics/TopicNameNotContainA/About-Log-Shipping--SQL-Server-.md)   
 [Log Shipping Tables and Stored Procedures](../../Topics/TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)