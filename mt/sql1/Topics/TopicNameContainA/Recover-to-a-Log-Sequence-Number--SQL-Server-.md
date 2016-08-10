---
title: "Recover to a Log Sequence Number (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Recover to a Log Sequence Number (SQL Server)
This topic is relevant only for databases that are using the full or bulk-logged recovery models.  
  
 You can use a log sequence number (LSN) to define the recovery point for a restore operation. However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.  
  
##  <a name="LSNs"></a> Overview of Log Sequence Numbers  
 LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored. When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken. Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.  
  
 Every record in the transaction log is uniquely identified by a log sequence number (LSN). LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.  
  
 The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences. Because LSNs are ordered, they can be compared for equality and inequality (that is, **<**, **>**, **=**, **<=**, **>=**). Such comparisons are useful when constructing restore sequences.  
  
> [!NOTE]  
>  LSNs are values of data type **numeric**(25,0). Arithmetic operations (for example, addition or subtraction) are not meaningful and must not be used with LSNs.  
  
 [&#91;Top&#93;](#Top)  
  
## Viewing LSNs Used by Backup and Restore  
 The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:  
  
-   [backupset](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)  
  
-   [backupfile](assetId:///f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac)  
  
-   [sys.database_files](assetId:///0f5b0aac-c17d-4e99-b8f7-d04efc9edf44); [sys.master_files](assetId:///803b22f2-0016-436b-a561-ce6f023d6b6a)  
  
-   [RESTORE HEADERONLY](assetId:///4b88e98c-49c4-4388-ab0e-476cc956977c)  
  
-   [RESTORE FILELISTONLY](assetId:///0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a)  
  
> [!NOTE]  
>  LSNs also appear in some message texts.  
  
## Transact-SQL Syntax for Restoring to an LSN  
 By using a [RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1) statement, you can stop at or immediately before the LSN, as follows:  
  
-   Use the WITH STOPATMARK **='**lsn:*<lsn_number>***'** clause, where lsn:*<lsnNumber\>* is a string that specifies that the log record that contains the specified LSN is the recovery point.  
  
     STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.  
  
-   Use the WITH STOPBEFOREMARK **='**lsn:*<lsn_number>***'** clause, where lsn:*<lsnNumber\>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.  
  
     STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.  
  
 Typically, a specific transaction is selected to be included or excluded. Although not required, in practice, the specified log record is a transaction-commit record.  
  
## Examples  
 The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Restore a Database Backup Using SSMS](../../Topics/TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
-   [Back Up a Transaction Log (SQL Server)](../../Topics/TopicNameContainA/Back-Up-a-Transaction-Log--SQL-Server-.md)  
  
-   [Restore a Transaction Log Backup (SQL Server)](../../Topics/TopicNameContainA/Restore-a-Transaction-Log-Backup--SQL-Server-.md)  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model (Transact-SQL)](../../Topics/TopicNameContainA/Restore-a-Database-to-the-Point-of-Failure-Under-the-Full-Recovery-Model--Transact-SQL-.md)  
  
-   [Restore a Database to a Marked Transaction (SQL Server Management Studio)](../../Topics/TopicNameContainA/Restore-a-Database-to-a-Marked-Transaction--SQL-Server-Management-Studio-.md)  
  
-   [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md)  
  
## See Also  
 [Apply Transaction Log Backups (SQL Server)](../../Topics/TopicNameNotContainA/Apply-Transaction-Log-Backups--SQL-Server-.md)   
 [The Transaction Log (SQL Server)](../../Topics/TopicNameNotContainA/The-Transaction-Log--SQL-Server-.md)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)