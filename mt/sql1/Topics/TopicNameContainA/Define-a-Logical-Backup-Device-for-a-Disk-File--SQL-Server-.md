---
title: "Define a Logical Backup Device for a Disk File (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# Define a Logical Backup Device for a Disk File (SQL Server)
This topic describes how to define a logical backup device for a disk file in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).  The initialization of the physical device occurs later, when a backup is written to the backup device.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To define a logical backup device for a disk file, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The logical device name must be unique among all the logical backup devices on the server instance. To view the existing logical device names, query the [sys.backup_devices](assetId:///457edaa4-aca1-4bd3-bf8d-734490b80fcd) catalog view.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   We recommend that a backup disk be a different disk than the database data and log disks. This is necessary to make sure that you can access the backups if the data or log disk fails.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires membership in the **diskadmin** fixed server role.  
  
 Requires permission to write to the disk.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To define a logical backup device for a disk file  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Server Objects**, and right-click **Backup Devices**.  
  
3.  Click **New Backup Device**. The **Backup Device** dialog box opens.  
  
4.  Enter a device name.  
  
5.  For the destination, click **File** and specify the full path of the file.  
  
6.  To define the new device, click **OK**.  
  
 To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box. For more information, see [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To define a logical backup for a disk file  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to use [sp_addumpdevice](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3) to define a logical backup device for a disk file. The example adds the disk backup device named `mydiskdump`, with the physical name `c:\dump\dump1.bak`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## See Also  
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)   
 [sys.backup_devices (Transact-SQL)](assetId:///457edaa4-aca1-4bd3-bf8d-734490b80fcd)   
 [sp_addumpdevice (Transact-SQL)](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3)   
 [sp_dropdevice (Transact-SQL)](assetId:///c8b07189-7c35-414b-acc1-45bd6e7e17c3)   
 [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md)   
 [View the Properties and Contents of a Logical Backup Device (SQL Server)](../../Topics/TopicNameContainA/View-the-Properties-and-Contents-of-a-Logical-Backup-Device--SQL-Server-.md)