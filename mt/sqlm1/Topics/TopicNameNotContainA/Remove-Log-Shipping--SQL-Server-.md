---
title: Remove Log Shipping (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
---
# Remove Log Shipping (SQL Server)
  This topic describes how to remove log shipping in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To remove log shipping, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 The log\-shipping stored procedures require membership in the **sysadmin** fixed server role.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove log shipping  
  
1.  Connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is currently the log shipping primary server and expand that instance.  
  
2.  Expand **Databases**, right\-click the log shipping primary database, and then click **Properties**.  
  
3.  Under **Select a page**, click **Transaction Log Shipping**.  
  
4.  Clear the **Enable this as a primary database in a log shipping configuration** check box.  
  
5.  Click **OK** to remove log shipping from this primary database.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To Remove Log Shipping  
  
1.  On the log shipping primary server, execute [sp\_delete\_log\_shipping\_primary\_secondary](../Topic/sp_delete_log_shipping_primary_secondary%20\(Transact-SQL\).md) to delete the information about the secondary database from the primary server.  
  
2.  On the log shipping secondary server, execute [sp\_delete\_log\_shipping\_secondary\_database](../Topic/sp_delete_log_shipping_secondary_database%20\(Transact-SQL\).md) to delete the secondary database.  
  
    > [!NOTE]  
    >  If there are no other secondary databases with the same secondary ID, **sp\_delete\_log\_shipping\_secondary\_primary** is invoked from **sp\_delete\_log\_shipping\_secondary\_database** and deletes the entry for the secondary ID and the copy and restore jobs.  
  
3.  On the log shipping primary server, execute **sp\_delete\_log\_shipping\_primary\_database** to delete information about the log shipping configuration from the primary server. This also deletes the backup job.  
  
4.  On the log shipping primary server, disable the backup job. For more information, see [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md).  
  
5.  On the log shipping secondary server, disable the copy and restore jobs.  
  
6.  Optionally, if you are no longer using the log shipping secondary database, you can delete it from the secondary server.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Upgrading Log Shipping to SQL Server 2016 &#40;Transact-SQL&#41;](../Topic/Upgrading%20Log%20Shipping%20to%20SQL%20Server%202016%20\(Transact-SQL\).md)  
  
-   [Configure Log Shipping &#40;SQL Server&#41;](../Topic/Configure%20Log%20Shipping%20\(SQL%20Server\).md)  
  
-   [Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Database%20to%20a%20Log%20Shipping%20Configuration%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20a%20Log%20Shipping%20Configuration%20\(SQL%20Server\).md)  
  
-   [Monitor Log Shipping &#40;Transact-SQL&#41;](../Topic/Monitor%20Log%20Shipping%20\(Transact-SQL\).md)  
  
-   [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](../Topic/Fail%20Over%20to%20a%20Log%20Shipping%20Secondary%20\(SQL%20Server\).md)  
  
-   [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md)  
  
## See Also  
 [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md)   
 [Log Shipping Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)  
  
  