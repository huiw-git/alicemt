---
title: "Select Backup Destination"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# Select Backup Destination
Use the **Select Backup Destination** dialog box to select a device as your backup destination. A backup destination can be either a disk or a logical backup device.  
  
 **To use SQL Server Management Studio to back up a database**  
  
-   [Create a Full Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md)  
  
-   [Create a Differential Database Backup (SQL Server)](../../Topics/TopicNameContainA/Create-a-Differential-Database-Backup--SQL-Server-.md)  
  
-   [Back Up Files and Filegroups (SQL Server)](../../Topics/TopicNameNotContainA/Back-Up-Files-and-Filegroups--SQL-Server-.md)  
  
-   [Back Up a Transaction Log (SQL Server)](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)  
  
## Options  
 The options of this dialog box depend on whether you are selecting a destination on disk or on tape.  
  
 **Destination on disk**  
 To specify a backup destination, choose one of the following options.  
  
|||  
|-|-|  
|**File name**|Choose this option to enter a local or remote file as the backup destination in the text box to:<br /><br /> Specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.<br /><br /> Specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name. For more information, see [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md).<br /><br /> <br /><br /> **\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes. For more information, see [RESTORE VERIFYONLY (Transact-SQL)](assetId:///cba3b6a0-b48e-4c94-812b-5b3cbb408bd6).|  
|**Backup device**|Choose this option to select a logical backup device.<br /><br /> Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Disk-File--SQL-Server-.md).|  
  
 **Destination on tape**  
 Specify a backup destination on a tape drive physically connected to the computer running the server (that is, the instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)]). Choose one of the following options.  
  
|||  
|-|-|  
|**Tape drive**|Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.<br /><br /> Note: Tape backup devices on remote computers are not valid backup destinations.|  
|**Backup device**|Choose this option to select an existing logical backup device. These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.<br /><br /> Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md).|  
  
## See Also  
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)   
 [Media Sets, Media Families, and Backup Sets (SQL Server)](../../Topics/TopicNameNotContainA/Media-Sets--Media-Families--and-Backup-Sets--SQL-Server-.md)