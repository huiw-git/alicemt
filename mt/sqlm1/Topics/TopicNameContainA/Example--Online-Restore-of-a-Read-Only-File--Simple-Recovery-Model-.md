---
title: Example: Online Restore of a Read-Only File (Simple Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
---
# Example: Online Restore of a Read-Only File (Simple Recovery Model)
  This topic is relevant for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases under the simple recovery model that contain a read\-only filegroup. Under the simple recovery model, a read\-only file can be restored online if a file backup exists that was taken since the file became read\-only for the last time.  
  
 In this example, a database named `adb` contains three filegroups. Filegroup `A` is read\/write, and filegroups `B` and `C` are read\-only. Initially, all of the filegroups are online. A read\-only file in filegroup `B`, `b1`, has to be restored. The database administrator can restore it by using a backup that was taken after the file became read\-only. For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.  
  
## Restore Sequence  
  
> [!NOTE]  
>  The syntax for an online restore sequence is the same as for an offline restore sequence.  
  
 To restore the file, the database administrator uses the following restore sequence:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 The file is now online.  
  
## Additional Examples  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  