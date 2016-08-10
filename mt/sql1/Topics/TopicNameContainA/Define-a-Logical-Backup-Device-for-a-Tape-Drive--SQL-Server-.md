---
title: "Define a Logical Backup Device for a Tape Drive (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Define a Logical Backup Device for a Tape Drive (SQL Server)
This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).  The initialization of the physical device occurs later, when a backup is written to the backup device.  
  
> [!NOTE]  
>  Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Avoid using this feature in new development work, and plan to modify applications that currently use this feature.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Security](#Security)  
  
-   **To define a logical backup device for a tape drive, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The tape drive or drives must be supported by the Microsoft Windows operating system.  
  
-   The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Backing up to remote tape devices is not supported.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the **diskadmin** fixed server role.  
  
 Requires permission to write to the disk.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To define a logical backup device for a tape drive  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Server Objects**, and then right-click **Backup Devices**.  
  
3.  Click **New Backup Device**, which opens the **Backup Device** dialog box.  
  
4.  Enter a device name.  
  
5.  For the destination, click **Tape** and select a tape drive that is not already associated with another backup device. If no such tape drives are available, the **Tape** option is inactive.  
  
6.  To define the new device, click **OK**.  
  
 To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box. For more information, see [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To define a logical backup device for a tape drive  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_addumpdevice](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3) to define a logical backup device for a tape. The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## See Also  
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [sys.backup_devices (Transact-SQL)](assetId:///457edaa4-aca1-4bd3-bf8d-734490b80fcd)   
 [sp_addumpdevice (Transact-SQL)](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3)   
 [sp_dropdevice (Transact-SQL)](assetId:///c8b07189-7c35-414b-acc1-45bd6e7e17c3)   
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)   
 [Define a Logical Backup Device for a Disk File (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Disk-File--SQL-Server-.md)   
 [View the Properties and Contents of a Logical Backup Device (SQL Server)](../../Topics/TopicNameContainA/View-the-Properties-and-Contents-of-a-Logical-Backup-Device--SQL-Server-.md)