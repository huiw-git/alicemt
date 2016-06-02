---
title: Example: Online Restore of a Read-Write File (Full Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
---
# Example: Online Restore of a Read-Write File (Full Recovery Model)
  This topic is relevant for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases under the full recovery model that contain multiple files or filegroups.  
  
 In this example, a database named `adb`, which uses the full recovery model, contains three filegroups. Filegroup `A` is read\/write, and filegroup `B` and filegroup `C` are read\-only. Initially, all of the filegroups are online.  
  
 File `a1` in filegroup `A` appears to be damaged, and the database administrator decides to restore it while the database remains online.  
  
> [!NOTE]  
>  Under the simple recovery model, online restore of read\/write data is not allowed.  
  
## Restore Sequences  
  
> [!NOTE]  
>  The syntax for an online restore sequence is the same as for an offline restore sequence.  
  
1.  Online restore of file `a1`.  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     At this point, file a1 is in the RESTORING state, and filegroup A is offline.  
  
2.  After restoring the file, the database administrator takes a new log backup to make sure that the point at which the file went offline is captured.  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  Online restore of log backups.  
  
     The administrator restores all the log backups taken since the restored file backup, ending with the latest log backup \(*log\_backup3*, taken in step 2\). After the last backup is restored, the database is recovered.  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     File `a1` is now online.  
  
## Additional Examples  
  
-   [Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Restore and Recovery Overview &#40;SQL Server&#41;](../Topic/Restore%20and%20Recovery%20Overview%20\(SQL%20Server\).md)   
 [Apply Transaction Log Backups &#40;SQL Server&#41;](../Topic/Apply%20Transaction%20Log%20Backups%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  