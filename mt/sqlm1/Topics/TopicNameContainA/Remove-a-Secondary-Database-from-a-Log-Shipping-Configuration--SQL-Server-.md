---
title: Remove a Secondary Database from a Log Shipping Configuration (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
---
# Remove a Secondary Database from a Log Shipping Configuration (SQL Server)
  This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To remove a log shipping secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The log\-shipping stored procedures require membership in the **sysadmin** fixed server role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove a log shipping secondary database  
  
1.  Connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is currently the log shipping primary server and expand that instance.  
  
2.  Expand **Databases**, right\-click the log shipping primary database, and then click **Properties**.  
  
3.  Under **Select a page**, click **Transaction Log Shipping**.  
  
4.  Under **Secondary server instances and databases**, click the database you want to remove.  
  
5.  Click **Remove**.  
  
6.  Click **OK** to update the configuration.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To Remove a Secondary Database  
  
1.  On the primary server, execute [sp\_delete\_log\_shipping\_primary\_secondary](../Topic/sp_delete_log_shipping_primary_secondary%20\(Transact-SQL\).md) to delete the information about the secondary database from the primary server.  
  
2.  On the secondary server, execute [sp\_delete\_log\_shipping\_secondary\_database](../Topic/sp_delete_log_shipping_secondary_database%20\(Transact-SQL\).md) to delete the secondary database.  
  
    > [!NOTE]  
    >  If there are no other secondary databases with the same secondary ID, **sp\_delete\_log\_shipping\_secondary\_primary** is invoked from **sp\_delete\_log\_shipping\_secondary\_database** and deletes the entry for the secondary ID and the copy and restore jobs.  
  
3.  On the secondary server, disable the copy and restore jobs. For more information, see [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Upgrading Log Shipping to SQL Server 2016 &#40;Transact-SQL&#41;](../Topic/Upgrading%20Log%20Shipping%20to%20SQL%20Server%202016%20\(Transact-SQL\).md)  
  
-   [Configure Log Shipping &#40;SQL Server&#41;](../Topic/Configure%20Log%20Shipping%20\(SQL%20Server\).md)  
  
-   [Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Database%20to%20a%20Log%20Shipping%20Configuration%20\(SQL%20Server\).md)  
  
-   [Remove Log Shipping &#40;SQL Server&#41;](../Topic/Remove%20Log%20Shipping%20\(SQL%20Server\).md)  
  
-   [View the Log Shipping Report &#40;SQL Server Management Studio&#41;](../Topic/View%20the%20Log%20Shipping%20Report%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Monitor Log Shipping &#40;Transact-SQL&#41;](../Topic/Monitor%20Log%20Shipping%20\(Transact-SQL\).md)  
  
-   [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](../Topic/Fail%20Over%20to%20a%20Log%20Shipping%20Secondary%20\(SQL%20Server\).md)  
  
## See Also  
 [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md)   
 [Log Shipping Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)  
  
  