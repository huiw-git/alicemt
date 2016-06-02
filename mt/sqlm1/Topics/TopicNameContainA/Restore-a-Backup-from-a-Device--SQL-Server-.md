---
title: Restore a Backup from a Device (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
---
# Restore a Backup from a Device (SQL Server)
  This topic describes how to restore a backup from a device in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
> [!NOTE]  
>  For information on SQL Server backup to the Windows Azure Blob storage service, see, [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To restore a backup from a device, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE. If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner \(**dbo**\) of the database \(for the FROM DATABASE\_SNAPSHOT option, the database always exists\).  
  
 RESTORE permissions are given to roles in which membership information is always readily available to the server. Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db\_owner** fixed database role do not have RESTORE permissions.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To restore a backup from a device  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, point to **Tasks**, and then click **Restore**.  
  
4.  Click the type of restore operation you want \(**Database**, **Files and Filegroups**, or **Transaction Log**\). This opens the corresponding restore dialog box.  
  
5.  On the **General** page, in the **Restore source** section, click **From device**.  
  
6.  Click the browse button for the **From device** text box, which opens the **Specify Backup** dialog box.  
  
7.  In the **Backup media** text box, select **Backup Device**, and click the **Add** button to open the **Select Backup Device** dialog box.  
  
8.  In the **Backup device** text box, select the device you want to use for the restore operation.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To restore a backup from a device  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  In the [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) statement, specify a logical or physical backup device to use for the backup operation. This example restores from a disk file that has the physical name `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## See Also  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20Backup%20Under%20the%20Simple%20Recovery%20Model%20\(Transact-SQL\).md)   
 [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)   
 [Restore a Differential Database Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)   
 [Restore a Database to a New Location &#40;SQL Server&#41;](../Topic/Restore%20a%20Database%20to%20a%20New%20Location%20\(SQL%20Server\).md)   
 [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)   
 [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)   
 [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
  