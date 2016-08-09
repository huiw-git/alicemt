---
title: "Monitor and troubleshoot data migration (Stretch Database)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06950858-8c02-4ec6-9c59-42b787316a2d
caps.latest.revision: 14
manager: jhubbard
---
# Monitor and troubleshoot data migration (Stretch Database)
To monitor data migration in Stretch Database Monitor, select **Tasks &#124; Stretch &#124; Monitor** for a database in SQL Server Management Studio .  
  
## Check the status of data migration in the Stretch Database Monitor  
 Select **Tasks &#124; Stretch &#124; Monitor** for a database in SQL Server Management Studio to open Stretch Database Monitor and monitor data migration.  
  
-   The top portion of the monitor displays general information about both the Stretch-enabled SQL Server database and the remote Azure database.  
  
-   The bottom portion of the monitor displays the status of data migration for each Stretch-enabled table in the database.  
  
 ![Stretch Database Monitor](../../Topics/TopicNameNotContainA/images/Stretch-monitor.PNG "Stretch)  
  
##  <a name="Migration"></a> Check the status of data migration in a dynamic management view  
 Open the dynamic management view **sys.dm_db_rda_migration_status** to see how many batches and rows of data have been migrated. For more info, see [sys.dm_db_rda_migration_status (Transact-SQL)](assetId:///faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd).  
  
##  <a name="Firewall"></a> Troubleshoot data migration  
 **Rows from my Stretch-enabled table are not being migrated to Azure. What’s the problem?**  
 There are several problems that can affect migration. Check the following things.  
  
-   Check network connectivity for the SQL Server computer.  
  
-   Check that the Azure firewall is not blocking your SQL Server from connecting to the remote endpoint.  
  
-   Check the dynamic management view **sys.dm_db_rda_migration_status** for the status of the latest batch. If an error has occurred, check the error_number, error_state, and error_severity values for the batch.  
  
    -   For more info about the view, see [sys.dm_db_rda_migration_status (Transact-SQL)](assetId:///faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd).  
  
    -   For more info about the content of a SQL Server error message, see [sys.messages (Transact-SQL)](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a).  
  
 **The Azure firewall is blocking connections from my local server.**  
 You may have to add a rule in the Azure firewall settings of the Azure server to let SQL Server communicate with the remote Azure server.  
  
## See Also  
 [Manage and troubleshoot Stretch Database](../../Topics/TopicNameNotContainA/Manage-and-troubleshoot-Stretch-Database.md)