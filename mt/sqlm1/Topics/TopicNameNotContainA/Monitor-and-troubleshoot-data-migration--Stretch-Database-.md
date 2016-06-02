---
title: Monitor and troubleshoot data migration (Stretch Database)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
---
# Monitor and troubleshoot data migration (Stretch Database)
  To monitor data migration in Stretch Database Monitor, select **Tasks | Stretch | Monitor** for a database in SQL Server Management Studio .  
  
## Check the status of data migration in the Stretch Database Monitor  
 Select **Tasks | Stretch | Monitor** for a database in SQL Server Management Studio to open Stretch Database Monitor and monitor data migration.  
  
-   The top portion of the monitor displays general information about both the Stretch\-enabled SQL Server database and the remote Azure database.  
  
-   The bottom portion of the monitor displays the status of data migration for each Stretch\-enabled table in the database.  
  
 ![Stretch Database Monitor](../../Images\Image\ImageNotContaina/Stretch-monitor.PNG "Stretch monitor")  
  
##  <a name="Migration"></a> Check the status of data migration in a dynamic management view  
 Open the dynamic management view **sys.dm\_db\_rda\_migration\_status** to see how many batches and rows of data have been migrated. For more info, see [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../Topic/sys.dm_db_rda_migration_status%20\(Transact-SQL\).md).  
  
##  <a name="Firewall"></a> Troubleshoot data migration  
 **Rows from my Stretch\-enabled table are not being migrated to Azure. What’s the problem?**  
 There are several problems that can affect migration. Check the following things.  
  
-   Check network connectivity for the SQL Server computer.  
  
-   Check that the Azure firewall is not blocking your SQL Server from connecting to the remote endpoint.  
  
-   Check the dynamic management view **sys.dm\_db\_rda\_migration\_status** for the status of the latest batch. If an error has occurred, check the error\_number, error\_state, and error\_severity values for the batch.  
  
    -   For more info about the view, see [sys.dm_db_rda_migration_status &#40;Transact-SQL&#41;](../Topic/sys.dm_db_rda_migration_status%20\(Transact-SQL\).md).  
  
    -   For more info about the content of a SQL Server error message, see [sys.messages &#40;Transact-SQL&#41;](../Topic/sys.messages%20\(Transact-SQL\).md).  
  
 **The Azure firewall is blocking connections from my local server.**  
 You may have to add a rule in the Azure firewall settings of the Azure server to let SQL Server communicate with the remote Azure server.  
  
## See Also  
 [Manage and troubleshoot Stretch Database](../../Topics\TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)  
  
  