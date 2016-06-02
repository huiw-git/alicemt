---
title: Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
---
# Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)
  This topic is relevant for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases under the simple recovery model that contain a read\-only filegroup.  
  
 A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read\/write, secondary filegroups.  
  
 In this example, a database named `adb`, which uses the simple recovery model, contains three filegroups. Filegroup `A` is read\/write, and filegroup `B` and filegroup `C` are read\-only. Initially, all of the filegroups are online.  
  
 The primary and filegroup `B` of database `adb` appear to be damaged; therefore, the database administrator decides to restore them by using a piecemeal restore sequence. Under the simple recovery model, all read\/write filegroups must be restored from the same partial backup. Although filegroup `A` is intact, it must be restored with the primary filegroup to make sure that they are consistent \(the database will be restored to the point in time defined by the end of the last partial backup\). Filegroup `C` is intact, but it must be recovered to bring it online. Filegroup `B`, although damaged, contains less critical data than Filegroup `C`; therefore, `B` will be restored last.  
  
## Restore Sequences  
  
> [!NOTE]  
>  The syntax for an online restore sequence is the same as for an offline restore sequence.  
  
1.  Partial restore of the primary and filegroup `A` from a partial backup.  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     At this point the primary filegroup and filegroup `A` are online. Files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.  
  
2.  Online recovery of filegroup `C`.  
  
     Filegroup `C` is consistent because the partial backup that was restored above was taken after filegroup `C` became read\-only, although the database was taken back in time by the restore. The database administrator recovers the filegroup `C`, without restoring it, to bring it online.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     At this point the primary and filegroups `A` and `C` are online. Files in filegroupB remain recovery pending, with the filegroup offline.  
  
3.  Online restore of filegroup `B.`  
  
     Files in filegroup `B` must be restored. The database administrator restores the backup of filegroup `B` taken after filegroup `B` became read\-only and before the partial backup.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     All filegroups are now online.  
  
## Additional Examples  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  