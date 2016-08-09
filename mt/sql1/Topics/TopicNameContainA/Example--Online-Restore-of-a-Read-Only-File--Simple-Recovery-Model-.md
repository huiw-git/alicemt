---
title: "Example: Online Restore of a Read-Only File (Simple Recovery Model)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
caps.latest.revision: 28
manager: jhubbard
---
# Example: Online Restore of a Read-Only File (Simple Recovery Model)
This topic is relevant for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases under the simple recovery model that contain a read-only filegroup. Under the simple recovery model, a read-only file can be restored online if a file backup exists that was taken since the file became read-only for the last time.  
  
 In this example, a database named `adb` contains three filegroups. Filegroup `A` is read/write, and filegroups `B` and `C` are read-only. Initially, all of the filegroups are online. A read-only file in filegroup `B`, `b1`, has to be restored. The database administrator can restore it by using a backup that was taken after the file became read-only. For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.  
  
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
  
-   [Example: Piecemeal Restore of Database (Simple Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Simple%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Database (Full Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Database%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)](../Topic/Example:%20Piecemeal%20Restore%20of%20Only%20Some%20Filegroups%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Write File (Full Recovery Model)](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Write%20File%20\(Full%20Recovery%20Model\).md)  
  
-   [Example: Online Restore of a Read-Only File (Full Recovery Model)](../Topic/Example:%20Online%20Restore%20of%20a%20Read-Only%20File%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [Online Restore (SQL Server)](../../Topics/TopicNameNotContainA/Online-Restore--SQL-Server-.md)   
 [Piecemeal Restores (SQL Server)](../../Topics/TopicNameNotContainA/Piecemeal-Restores--SQL-Server-.md)   
 [File Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/File-Restores--Simple-Recovery-Model-.md)   
 [Restore and Recovery Overview (SQL Server)](../../Topics/TopicNameNotContainA/Restore-and-Recovery-Overview--SQL-Server-.md)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)