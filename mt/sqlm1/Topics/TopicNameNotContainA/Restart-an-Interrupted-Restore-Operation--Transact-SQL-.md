---
title: Restart an Interrupted Restore Operation (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
---
# Restart an Interrupted Restore Operation (Transact-SQL)
  This topic explains how to restart an interrupted restore operation.  
  
### To restart an interrupted restore operation  
  
1.  Execute the interrupted RESTORE statement again, specifying:  
  
    -   The same clauses used in the original RESTORE statement.  
  
    -   The RESTART clause.  
  
## Example  
 This example restarts an interrupted restore operation.  
  
```tsql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## See Also  
 [Complete Database Restores &#40;Full Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Full%20Recovery%20Model\).md)   
 [Complete Database Restores &#40;Simple Recovery Model&#41;](../Topic/Complete%20Database%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  