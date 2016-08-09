---
title: "Back Up to a Mirrored Media Set (Transact-SQL)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 6
caps.handback.revision: 0
manager: jhubbard
---
# Back Up to a Mirrored Media Set (Transact-SQL)
This topic describes how to use the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)][BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database. In your BACKUP statement, specify the first mirror in the TO clause. Then, specify each mirror in its own MIRROR TO clause. The TO and MIRROR TO clauses must specify the same number and type of backup devices.  
  
## Example  
 The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database to both mirrors.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## Related Tasks  
 **To restore from a mirrored backup**  
  
-   [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)  
  
## See Also  
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [Mirrored Backup Media Sets (SQL Server)](../../Topics/TopicNameNotContainA/Mirrored-Backup-Media-Sets--SQL-Server-.md)