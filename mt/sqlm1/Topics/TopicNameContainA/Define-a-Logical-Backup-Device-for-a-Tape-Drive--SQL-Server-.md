---
title: Define a Logical Backup Device for a Tape Drive (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
---
# Define a Logical Backup Device for a Tape Drive (SQL Server)
  This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. A logical device is a user\-defined name that points to a specific physical backup device \(a disk file or tape drive\).  The initialization of the physical device occurs later, when a backup is written to the backup device.  
  
> [!NOTE]  
>  Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Avoid using this feature in new development work, and plan to modify applications that currently use this feature.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To define a logical backup device for a tape drive, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The tape drive or drives must be supported by the Microsoft Windows operating system.  
  
-   The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Backing up to remote tape devices is not supported.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the **diskadmin** fixed server role.  
  
 Requires permission to write to the disk.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To define a logical backup device for a tape drive  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Server Objects**, and then right\-click **Backup Devices**.  
  
3.  Click **New Backup Device**, which opens the **Backup Device** dialog box.  
  
4.  Enter a device name.  
  
5.  For the destination, click **Tape** and select a tape drive that is not already associated with another backup device. If no such tape drives are available, the **Tape** option is inactive.  
  
6.  To define the new device, click **OK**.  
  
 To back up to this new device, add it to the **Back up to:** field in the **Back up Database** \(**General**\) dialog box. For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To define a logical backup device for a tape drive  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp\_addumpdevice](../Topic/sp_addumpdevice%20\(Transact-SQL\).md) to define a logical backup device for a tape. The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](../Topic/sys.backup_devices%20\(Transact-SQL\).md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../Topic/sp_addumpdevice%20\(Transact-SQL\).md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../Topic/sp_dropdevice%20\(Transact-SQL\).md)   
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)   
 [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md)   
 [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
  