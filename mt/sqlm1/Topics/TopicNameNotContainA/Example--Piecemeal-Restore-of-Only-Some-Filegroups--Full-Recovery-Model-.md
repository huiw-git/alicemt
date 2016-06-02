---
title: Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
---
# Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)
  This topic is relevant for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases under the full recovery model that contain multiple files or filegroups.  
  
 A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read\/write, secondary filegroups.  
  
 In this example, a database named `adb`, which uses the full recovery model, contains three filegroups. Filegroup `A` is read\/write, and filegroup `B` and filegroup `C` are read\-only. Initially, all of the filegroups are online.  
  
 The primary and filegroup `B` of database `adb` appear to be damaged. The primary filegroup is fairly small and can be restored quickly. The database administrator decides to restore them by using a piecemeal restore sequence. First, the primary filegroup and the subsequent transaction logs are restored the database is recovered.  
  
 The intact filegroups `A` and `C` contain critical data. Therefore, they will be recovered next to bring them online as quickly as possible. Finally, the damaged secondary filegroup, `B`, is restored and recovered.  
  
## Restore Sequences:  
  
> [!NOTE]  
>  The syntax for an online restore sequence is the same as for an offline restore sequence.  
  
1.  Create a tail log backup of database `adb`. This step is essential to make the intact filegroups `A` and `C` current with the recovery point of the database.  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  Partial restore of the primary filegroup.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     At this point the primary is online. Files in filegroups `A`, `B`, and `C` are recovery pending, and the filegroups are offline.  
  
3.  Online restore of filegroups `A` and `C`.  
  
     Because their data is undamaged, these filegroups do not have to be restored from a backup, but they do have to be recovered to bring them online.  
  
     The database administrator recovers `A` and `C` immediately.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     At this point the primary and filegroups `A` and `C` are online. Files in filegroup `B` remain recovery pending, with the filegroup offline.  
  
4.  Online restore of filegroup `B`.  
  
     Files in filegroup `B` are restored any time thereafter.  
  
    > [!NOTE]  
    >  The backup of filegroup `B` was taken after the filegroup became read\-only; therefore, these files do not have to be rolled forward.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     All filegroups are now online.  
  
## Additional Examples  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [Apply Transaction Log Backups &#40;SQL Server&#41;](../Topic/Apply%20Transaction%20Log%20Backups%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  