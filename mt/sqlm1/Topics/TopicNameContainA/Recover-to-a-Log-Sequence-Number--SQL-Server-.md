---
title: Recover to a Log Sequence Number (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
---
# Recover to a Log Sequence Number (SQL Server)
  This topic is relevant only for databases that are using the full or bulk\-logged recovery models.  
  
 You can use a log sequence number \(LSN\) to define the recovery point for a restore operation. However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.  
  
##  <a name="LSNs"></a> Overview of Log Sequence Numbers  
 LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored. When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken. Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.  
  
 Every record in the transaction log is uniquely identified by a log sequence number \(LSN\). LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.  
  
 The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences. Because LSNs are ordered, they can be compared for equality and inequality \(that is, **\<**, **\>**, **\=**, **\<\=**, **\>\=**\). Such comparisons are useful when constructing restore sequences.  
  
> [!NOTE]  
>  LSNs are values of data type **numeric**\(25,0\). Arithmetic operations \(for example, addition or subtraction\) are not meaningful and must not be used with LSNs.  
  
 [&#91;Top&#93;](#Top)  
  
## Viewing LSNs Used by Backup and Restore  
 The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:  
  
-   [backupset](../Topic/backupset%20\(Transact-SQL\).md)  
  
-   [backupfile](../Topic/backupfile%20\(Transact-SQL\).md)  
  
-   [sys.database\_files](../Topic/sys.database_files%20\(Transact-SQL\).md); [sys.master\_files](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
-   [RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)  
  
-   [RESTORE FILELISTONLY](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  LSNs also appear in some message texts.  
  
## Transact\-SQL Syntax for Restoring to an LSN  
 By using a [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) statement, you can stop at or immediately before the LSN, as follows:  
  
-   Use the WITH STOPATMARK **\='**lsn:*\<lsn\_number\>***'** clause, where lsn:*\<lsnNumber\>* is a string that specifies that the log record that contains the specified LSN is the recovery point.  
  
     STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.  
  
-   Use the WITH STOPBEFOREMARK **\='**lsn:*\<lsn\_number\>***'** clause, where lsn:*\<lsnNumber\>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.  
  
     STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.  
  
 Typically, a specific transaction is selected to be included or excluded. Although not required, in practice, the specified log record is a transaction\-commit record.  
  
## Examples  
 The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
-   [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20to%20the%20Point%20of%20Failure%20Under%20the%20Full%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;](../Topic/Restore%20a%20Database%20to%20a%20Marked%20Transaction%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md)  
  
## See Also  
 [Apply Transaction Log Backups &#40;SQL Server&#41;](../Topic/Apply%20Transaction%20Log%20Backups%20\(SQL%20Server\).md)   
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  