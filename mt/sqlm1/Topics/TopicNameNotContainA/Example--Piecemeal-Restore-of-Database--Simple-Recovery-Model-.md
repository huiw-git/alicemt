---
title: Example: Piecemeal Restore of Database (Simple Recovery Model)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
---
# Example: Piecemeal Restore of Database (Simple Recovery Model)
  A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read\/write, secondary filegroups.  
  
 In this example, database `adb` is restored to a new computer after a disaster. The database is using the simple recovery model. Before the disaster, all the filegroups are online. Filegroups `A` and `C` are read\/write, and filegroup `B` is read\-only. Filegroup `B` became read\-only before the most recent partial backup, which contains the primary filegroup and the read\/write secondary filegroups, `A` and `C`. After filegroup `B` became read\-only, a separate file backup of filegroup `B` was taken.  
  
## Restore Sequences  
  
1.  Partial restore of the primary and filegroups `A` and `C`.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     At this point, the primary and filegroups `A` and `C` are online. All files in filegroup `B` are recovery pending, and the filegroup is offline.  
  
2.  Online restore of filegroup `B`.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     All filegroups are now online.  
  
## Additional Examples  
  
-   [Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
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
  
  