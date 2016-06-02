---
title: View the Contents of a Backup Tape or File (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
---
# View the Contents of a Backup Tape or File (SQL Server)
  This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!NOTE]  
>  Support for tape backup devices will be removed in a future version of SQL Server. Avoid using this feature in new development work, and plan to modify applications that currently use this feature.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the content of a backup tape or file, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md).  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Database%20Permissions%20\(Transact-SQL\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the content of a backup tape or file  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database you want to backup, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.  
  
4.  In the **Destination** section of the **General** page, click either **Disk** or **Tape**. In the **Back up to** list box, look for the disk file or tape you want.  
  
     If the disk file or tape is not displayed in the list\-box, click **Add**. Select a file name or tape drive. To add it to the **Back up to** list\-box, click **OK**.  
  
5.  In the **Back up to** list\-box, select the path of the disk or tape drive you want to view, and click **Contents**. This opens the **Device Contents** dialog box.  
  
6.  The right\-hand pane displays information about the media set and backup sets on the selected tape or file.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view the content of a backup tape or file  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md) statement. This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.  
  
```tsql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## See Also  
 [backupfilegroup &#40;Transact-SQL&#41;](../Topic/backupfilegroup%20\(Transact-SQL\).md)   
 [backupfile &#40;Transact-SQL&#41;](../Topic/backupfile%20\(Transact-SQL\).md)   
 [backupset &#40;Transact-SQL&#41;](../Topic/backupset%20\(Transact-SQL\).md)   
 [backupmediaset &#40;Transact-SQL&#41;](../Topic/backupmediaset%20\(Transact-SQL\).md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../Topic/backupmediafamily%20\(Transact-SQL\).md)   
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)   
 [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md)   
 [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Tape%20Drive%20\(SQL%20Server\).md)  
  
  