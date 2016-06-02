---
title: Backup Device (Media Contents Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
---
# Backup Device (Media Contents Page)
  Use the **Backup Device** dialog box to view the backup information. This information describes the device, the media, the media set, and the backup set or sets.  
  
 **To use SQL Server Management Studio to view the contents of a backup device**  
  
-   [View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../Topic/View%20the%20Contents%20of%20a%20Backup%20Tape%20or%20File%20\(SQL%20Server\).md)  
  
-   [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../Topic/View%20the%20Properties%20and%20Contents%20of%20a%20Logical%20Backup%20Device%20\(SQL%20Server\).md)  
  
## Options  
 View information about the individual media, media set, and backup sets.  
  
 **Media**  
 A disk or set of tapes on which backup information is stored.  
  
 **Media sequence**  
 Lists the media sequence number, the family sequence number, and the mirror identifier, if any. The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used. The initial backup media is tagged with 1, the second \(the first continuation tape\) is tagged with 2, and so forth. When the backup set is restored, the media sequence numbers ensure that the operator restoring the backup mounts the correct media in the correct order.  
  
 **Created on**  
 Displays the creation date and time of the media set.  
  
 **Media Set**  
 A media set is an ordered collection of backup media to which one or more backup operations have written by using a constant number of backup devices.  
  
 **Name**  
 Displays the name of the media set, if any.  
  
 **Description**  
 Displays the description of the media set, if any.  
  
 **Media family count**  
 Displays the number of families in the media set. Each media set is a collection of one or more media families. All the output to a given single backup device \(or group of mirrored backup devices\) forms a single media family. Each media set contains one media family per separate device \(or group of mirrored devices\); for instance, if a media set uses two non\-mirrored backup devices, the media set contains two media families.  
  
 **Backup sets**  
 Displays information about the backup set or sets contained on the media. A backup set is the result of a successful backup operation, whose content is distributed among the media on the set of backup devices.  
  
|Header|Values|  
|------------|------------|  
|**Name**|The name of the backup set.|  
|**Type**|The backed\-up object: Database, File, or *\<blank\>* \(for transaction logs\).|  
|**Component**|The type of backup performed: Full, Differential or Transaction Log.|  
|**Server**|The name of the instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] that performed the backup operation.|  
|**Database**|The name of the database that was backed up.|  
|**Position**|The position of the backup set in the volume.|  
|**Date**|The date and time when the backup operation finished, presented in the regional setting of the client.|  
|**Size**|The size of the backup set in bytes.|  
|**User Name**|The name of the user who performed the backup operation.|  
|**Expiration**|The date and time the backup set expires.|  
  
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
  
  