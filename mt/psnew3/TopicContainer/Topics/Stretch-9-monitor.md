---
title: Stretch 9 monitor
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 198ea3db-a621-49ee-a88b-129bd946d62f
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
# Stretch 9 monitor
To monitor data migration in Stretch Database Monitor, select **Tasks &#124; Stretch &#124; Monitor** for a database in SQL Server Management Studio .  
  
## Check the status of data migration in the Stretch Database Monitor  
 Select **Tasks &#124; Stretch &#124; Monitor** for a database in SQL Server Management Studio to open Stretch Database Monitor and monitor data migration.  
  
-   The top portion of the monitor displays general information about both the Stretch\-enabled SQL Server database and the remote Azure database.  
  
-   The bottom portion of the monitor displays the status of data migration for each Stretch\-enabled table in the database.  
  
 184b00e3-7cb0-4f9e-8935-711157e420da  
  
##  <a name="Migration"></a> Check the status of data migration in a dynamic management view  
 Open the dynamic management view **sys.dm\_db\_rda\_migration\_status** to see how many batches and rows of data have been migrated. For more info, see [sys.dm\_db\_rda\_migration\_status \(Transact\-SQL\)](assetId:///faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd).  
  
##  <a name="Firewall"></a> Troubleshoot data migration  
 **The Azure firewall is blocking connections from my local server.**  
 You may have to add a rule in the Azure firewall settings of the SQL Database server to let SQL Server communicate with the remote Azure server. For more info, see [How to: Configure Firewall Settings \(Azure SQL Database\)](https://msdn.microsoft.com/library/azure/jj553530.aspx).  
  
 **Rows from my Stretch\-enabled table are not being migrated to Azure. What’s the problem?**  
 There are several problems that can affect migration. Check the following things.  
  
-   Check network connectivity for the SQL Server computer.  
  
-   Check that the Azure firewall is not blocking your SQL Server from connecting to the remote endpoint. To configure Azure Firewall rules, see [How to: Configure Firewall Settings \(Azure SQL Database\)](https://msdn.microsoft.com/en-us/library/azure/jj553530.aspx).  
  
-   Check the dynamic management view **sys.dm\_db\_rda\_migration\_status** for the status of the latest batch. If an error has occurred, check the error\_number, error\_state, and error\_severity values for the batch.  
  
    -   For more info about the view, see [sys.dm\_db\_rda\_migration\_status \(Transact\-SQL\)](assetId:///faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd).  
  
    -   For more info about the content of a SQL Server error message, see [sys.messages \(Transact\-SQL\)](assetId:///8c16ecdf-68f4-4a2a-b594-086e3344e58a).  
  
## See Also  
 [Manage and troubleshoot Stretch Database](assetId:///6334db3e-9297-44df-8d53-211187a95520)