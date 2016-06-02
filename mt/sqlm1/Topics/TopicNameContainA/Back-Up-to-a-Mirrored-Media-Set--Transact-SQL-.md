---
title: Back Up to a Mirrored Media Set (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
---
# Back Up to a Mirrored Media Set (Transact-SQL)
  This topic describes how to use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)][BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. In your BACKUP statement, specify the first mirror in the TO clause. Then, specify each mirror in its own MIRROR TO clause. The TO and MIRROR TO clauses must specify the same number and type of backup devices.  
  
## Example  
 The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database to both mirrors.  
  
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
  
-   [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Mirrored Backup Media Sets &#40;SQL Server&#41;](../Topic/Mirrored%20Backup%20Media%20Sets%20\(SQL%20Server\).md)  
  
  