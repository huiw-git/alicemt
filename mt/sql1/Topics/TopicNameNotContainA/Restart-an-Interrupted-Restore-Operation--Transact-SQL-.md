---
title: "Restart an Interrupted Restore Operation (Transact-SQL)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
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
 [Complete Database Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Full-Recovery-Model-.md)   
 [Complete Database Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/Complete-Database-Restores--Simple-Recovery-Model-.md)   
 [RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)