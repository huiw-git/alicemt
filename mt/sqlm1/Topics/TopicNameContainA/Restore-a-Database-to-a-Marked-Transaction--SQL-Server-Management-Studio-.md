---
title: Restore a Database to a Marked Transaction (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
---
# Restore a Database to a Marked Transaction (SQL Server Management Studio)
  When a database is in the restoring state, you can use the **Restore Transaction Log** dialog box to restore the database to a marked transaction in the available log backups.  
  
> [!NOTE]  
>  For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](../Topic/Use%20Marked%20Transactions%20to%20Recover%20Related%20Databases%20Consistently%20\(Full%20Recovery%20Model\).md) and [Recovery of Related  Databases That Contain Marked Transaction](../../Topics\TopicNameNotContainA/Recovery-of-Related--Databases-That-Contain-Marked-Transaction.md).  
  
### To restore a marked transaction  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, point to **Tasks**, and then click **Restore**.  
  
4.  Click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.  
  
5.  On the **General** page, in the **Restore To** section, select **Marked transaction**, which opens the **Select Marked Transaction** dialog box. This dialog box displays a grid listing the marked transactions available in the selected transaction log backups.  
  
     By default, the restore is up to, but excluding, the marked transaction. To restore the marked transaction also, select **Include marked transaction**.  
  
     The following table lists the column headers of the grid and describes their values.  
  
    |Header|Value|  
    |------------|-----------|  
    |\<blank\>|Displays a checkbox for selecting the mark.|  
    |**Transaction Mark**|Name of the marked transaction specified by the user when the transaction was committed.|  
    |**Date**|Date and time of the transaction when it was committed. Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.|  
    |**Description**|Description of marked transaction specified by the user when the transaction was committed \(if any\).|  
    |**LSN**|Log sequence number of the marked transaction.|  
    |**Database**|Name of the database where the marked transaction was committed.|  
    |**User Name**|Name of the database user who committed the marked transaction.|  
  
## See Also  
 [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)   
 [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)  
  
  