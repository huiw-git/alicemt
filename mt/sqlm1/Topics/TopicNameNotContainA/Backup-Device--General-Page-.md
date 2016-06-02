---
title: Backup Device (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
---
# Backup Device (General Page)
  Use the **General** page to specify or view the general properties of a logical backup device.  
  
 **To use SQL Server Management Studio to view the contents of a backup device**  
  
-   [View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../Topic/View%20the%20Contents%20of%20a%20Backup%20Tape%20or%20File%20\(SQL%20Server\).md)  
  
-   [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
## Options  
 **Device name**  
 View the name of an existing logical backup device or specify the name of a new logical backup device.  
  
 **Tape**  
 View or select the destination tape device in the **Tape** list. This option is available only if a tape drive is attached to the computer that is running the instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  
  
> [!NOTE]  
>  Tape backup devices on remote computers are not valid backup destinations.  
  
 **File**  
 View the destination file of an existing logical backup device, or specify a destination file for a new logical backup device.  
  
-   For an existing logical backup device, the path of the backup file is displayed. The **File** field is not editable, and the Browse button is unavailable.  
  
-   For a new logical backup device, you must supply the path of the backup file for which you are defining the logical backup device. This file does not have to exist yet.  
  
     To specify a local backup file, you can click the Browse button to the right of the **File** text box. Then, in the **Locate Database Files** dialog box, you can navigate to any location on any of the fixed drives on the computer running the server instance. If the backup file does not exist yet, you must enter the filename you want to use in the **File name** field of that dialog box.  
  
     Alternatively, you can edit the **File** field manually to override the default path, file name, and extension. To specify a remote file as your backup destination, enter its fully qualified universal naming convention \(UNC\) name. For more information, see [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md).  
  
    > [!IMPORTANT]  
    >  Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes. For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md).  
  
## Remarks  
 The backups on a set of one or more backup devices compose a single media set. A *media set* is an ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices. For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md).  
  
 The physical backup device corresponding to a logical backup device is initialized when the first backup in the media set is written to the logical backup device. If the physical backup device is a file that does not exist yet, it is created at that time.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Disk%20File%20\(SQL%20Server\).md)  
  
-   [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](../Topic/Define%20a%20Logical%20Backup%20Device%20for%20a%20Tape%20Drive%20\(SQL%20Server\).md)  
  
-   [Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;](../Topic/Specify%20a%20Disk%20or%20Tape%20As%20a%20Backup%20Destination%20\(SQL%20Server\).md)  
  
-   [Delete a Backup Device &#40;SQL Server&#41;](../Topic/Delete%20a%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Set the Expiration Date on a Backup &#40;SQL Server&#41;](../Topic/Set%20the%20Expiration%20Date%20on%20a%20Backup%20\(SQL%20Server\).md)  
  
-   [View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../Topic/View%20the%20Contents%20of%20a%20Backup%20Tape%20or%20File%20\(SQL%20Server\).md)  
  
-   [View the Data and Log Files in a Backup Set &#40;SQL Server&#41;](../Topic/View%20the%20Data%20and%20Log%20Files%20in%20a%20Backup%20Set%20\(SQL%20Server\).md)  
  
-   [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
-   [Restore a Backup from a Device &#40;SQL Server&#41;](../Topic/Restore%20a%20Backup%20from%20a%20Device%20\(SQL%20Server\).md)  
  
## See Also  
 [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md)   
 [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)  
  
  