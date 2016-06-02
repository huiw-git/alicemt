---
title: View the Data and Log Files in a Backup Set (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
---
# View the Data and Log Files in a Backup Set (SQL Server)
  This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the data and log files in a backup set, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Database%20Permissions%20\(Transact-SQL\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the data and log files in a backup set  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.  
  
4.  In the **Select a Page** pane, click **Files**.  
  
5.  Look in the **Database files** grid for a list of the data and log files and their properties.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view the data and log files in a backup set  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE FILELISTONLY](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md) statement. This example returns information about the second backup set \(`FILE=2`\) on the `AdventureWorksBackups` backup device.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## See Also  
 [backupfilegroup &#40;Transact-SQL&#41;](../Topic/backupfilegroup%20\(Transact-SQL\).md)   
 [backupfile &#40;Transact-SQL&#41;](../Topic/backupfile%20\(Transact-SQL\).md)   
 [backupset &#40;Transact-SQL&#41;](../Topic/backupset%20\(Transact-SQL\).md)   
 [backupmediaset &#40;Transact-SQL&#41;](../Topic/backupmediaset%20\(Transact-SQL\).md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../Topic/backupmediafamily%20\(Transact-SQL\).md)   
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)  
  
  