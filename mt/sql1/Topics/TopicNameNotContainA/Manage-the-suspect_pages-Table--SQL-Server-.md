---
title: "Manage the suspect_pages Table (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
caps.latest.revision: 55
caps.handback.revision: 0
manager: jhubbard
---
# Manage the suspect_pages Table (SQL Server)
This topic describes how to manage the **suspect_pages** table in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. The **suspect_pages** table is used for maintaining information about suspect pages, and is relevant in helping to decide whether a restore is necessary. The [suspect_pages](assetId:///119c8d62-eea8-44fb-bf72-de469c838c50) table resides in the [msdb database](../../Topics/TopicNameNotContainA/msdb-Database.md).  
  
 A page is considered "suspect" when the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] encounters one of the following errors when it tries to read a data page:  
  
-   An [823 error](assetId:///0d9fce3c-3772-46ce-a7a3-4f4988dc6cae) that was caused by a cyclic redundancy check (CRC) issued by the operating system, such as a disk error (certain hardware errors)  
  
-   An [824 error](assetId:///2aa22246-2712-4fdb-9744-36e7e6f3175e), such as a torn page (any logical error)  
  
 The page ID of every suspect page is recorded in the **suspect_pages** table. The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] records any suspect pages encountered during regular processing, such as the following:  
  
-   A query has to read a page.  
  
-   During a DBCC CHECKDB operation.  
  
-   During a backup operation.  
  
 The **suspect_pages** table is also updated as necessary during a restore operation, a DBCC repair operation, or a drop database operation.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To manage the suspect_pages table, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   **Errors Recorded in suspect_pages Table**  
  
     The **suspect_pages** table contains one row per page that failed with an 824 error, up to a limit of 1,000 rows. The following table shows errors logged in the **event_type** column of the **suspect_pages** table.  
  
    |Error description|**event_type** value|  
    |-----------------------|---------------------------|  
    |823 error caused by an operating system CRC error  or 824 error other than a bad checksum or a torn page (for example, a bad page ID)|1|  
    |Bad checksum|2|  
    |Torn page|3|  
    |Restored (The page was restored after it was marked bad)|4|  
    |Repaired (DBCC repaired the page)|5|  
    |Deallocated by DBCC|7|  
  
     The **suspect_pages** table also records transient errors.  Sources of transient errors include an I/O error (for example, a cable was disconnected) or a page that temporarily fails a repeated checksum test.  
  
-   **How the Database Engine Updates the suspect_pages Table**  
  
     The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] takes the following actions on the **suspect_pages** table:  
  
    -   If the table is not full, it is updated for every 824 error, to indicate that an error has occurred, and the error counter is incremented. If a page has an error after it is fixed by being repaired, restored, or deallocated, its **number_of_errors** count is incremented and its **last_update** column is updated  
  
    -   After a listed page is fixed by a restore or a repair operation, the operation updates the **suspect_pages** row to indicate that the page is repaired (**event_type** = 5) or restored (**event_type** = 4).  
  
    -   If a DBCC check is run, the check marks any error-free pages as repaired (**event_type** = 5) or deallocated (**event_type** = 7).  
  
-   **Automatic Updates to the suspect_pages Table**  
  
     A database mirroring partner or Always On availability replica updates the **suspect_pages** table after an attempt to read a page from a data file fails for one of the following reasons.  
  
    -   An 823 error that is caused by an operating system CRC error.  
  
    -   An 824 error (logical corruption such as a torn page).  
  
     The following actions also automatically update rows in the **suspect_pages** table.  
  
    -   DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS updates the **suspect_pages** table to indicate each page that it has deallocated or repaired.  
  
    -   A full, file, or page RESTORE marks the page entries as restored.  
  
     The following actions automatically delete rows from the **suspect_pages** table.  
  
    -   ALTER DATABASE REMOVE FILE  
  
    -   DROP DATABASE  
  
-   **Maintenance Role of the Database Administrator**  
  
     Database administrators are responsible for managing the table, primarily by deleting old rows. The **suspect_pages** table is limited in size, and if it fills, new errors are not logged. To prevent this table from filling up, the database administrator or system administrator must manually clear out old entries from this table by deleting rows. Therefore, we recommend that you periodically delete or archive rows that have an **event_type** of restored or repaired, or rows that have an old **last_update** value.  
  
     To monitor the activity on the suspect_pages table, you can use the [Database Suspect Data Page Event Class](../../Topics/TopicNameNotContainA/Database-Suspect-Data-Page-Event-Class.md). Rows are sometimes added to the **suspect_pages** table because of transient errors. If many rows are being added to the table, however, a problem probably exists with the I/O subsystem. If you notice a sudden increase in the number of rows being added to the table, we recommend that you investigate possible problems in your I/O subsystem.  
  
     A database administrator can also insert or update records. For example, updating a row might useful when the database administrator knows that a particular suspect page is actually intact, but wants to preserve the record for a while.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Anyone with access to **msdb** can read the data in the **suspect_pages** table. Anyone with UPDATE permission on the suspect_pages table can update its records. Members the **db_owner** fixed database role on **msdb** or the **sysadmin** fixed server role can insert, update, and delete records.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To manage the suspect_pages table  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], expand that instance, and then expand **Databases**.  
  
2.  Expand **System Databases**, expand **msdb**, expand **Tables**, and then expand **System Tables**.  
  
3.  Expand **dbo.suspect_pages** and right-click **Edit Top 200 Rows**.  
  
4.  In the query window, edit, update, or delete the rows that you want.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To manage the suspect_pages table  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following examples into the query window and click **Execute**. This example deletes some of the rows from the `suspect_pages` table.  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 This example returns the bad pages in the `suspect_pages` table.  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## See Also  
 [DROP DATABASE (Transact-SQL)](assetId:///477396a9-92dc-43c9-9b97-42c8728ede8e)   
 [RESTORE (Transact-SQL)](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1)   
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [DBCC (Transact-SQL)](assetId:///c6da8c04-5b6b-459a-9f76-110c92ca8b29)   
 [Restore Pages (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Pages--SQL-Server-.md)   
 [suspect_pages (Transact-SQL)](assetId:///119c8d62-eea8-44fb-bf72-de469c838c50)   
 [MSSQLSERVER_823](assetId:///0d9fce3c-3772-46ce-a7a3-4f4988dc6cae)   
 [MSSQLSERVER_824](assetId:///2aa22246-2712-4fdb-9744-36e7e6f3175e)