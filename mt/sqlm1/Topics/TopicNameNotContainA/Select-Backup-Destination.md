---
title: Select Backup Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
---
# Select Backup Destination
  Use the **Select Backup Destination** dialog box to select a device as your backup destination. A backup destination can be either a disk or a logical backup device.  
  
 **To use SQL Server Management Studio to back up a database**  
  
-   [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
## Options  
 The options of this dialog box depend on whether you are selecting a destination on disk or on tape.  
  
 **Destination on disk**  
 To specify a backup destination, choose one of the following options.  
  
|||  
|-|-|  
|**File name**|Choose this option to enter a local or remote file as the backup destination in the text box to:<br /><br /> Specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.<br /><br /> Specify a remote file as your backup destination, enter its fully qualified universal naming convention \(UNC\) name. For more information, see [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md).<br /><br /> <br /><br /> **\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes. For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md).|  
|**Backup device**|Choose this option to select a logical backup device.<br /><br /> Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md).|  
  
 **Destination on tape**  
 Specify a backup destination on a tape drive physically connected to the computer running the server \(that is, the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]\). Choose one of the following options.  
  
|||  
|-|-|  
|**Tape drive**|Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.<br /><br /> Note: Tape backup devices on remote computers are not valid backup destinations.|  
|**Backup device**|Choose this option to select an existing logical backup device. These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.<br /><br /> Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Tape%20Drive%20\(SQL%20Server\).md).|  
  
## See Also  
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)   
 [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
  
  