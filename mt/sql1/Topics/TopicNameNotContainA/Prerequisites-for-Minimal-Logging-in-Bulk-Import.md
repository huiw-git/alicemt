---
title: "Prerequisites for Minimal Logging in Bulk Import"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
caps.latest.revision: 48
caps.handback.revision: 0
manager: jhubbard
---
# Prerequisites for Minimal Logging in Bulk Import
For a database under the full recovery model, all row-insert operations that are performed by bulk import are fully logged in the transaction log. Large data imports can cause the transaction log to fill rapidly if the full recovery model is used. In contrast, under the simple recovery model or bulk-logged recovery model, minimal logging of bulk-import operations reduces the possibility that a bulk-import operation will fill the log space. Minimal logging is also more efficient than full logging.  
  
> [!NOTE]  
>  The bulk-logged recovery model is designed to temporarily replace the full recovery model during large bulk operations.  
  
## Table Requirements for Minimally Logging Bulk-Import Operations  
 Minimal logging requires that the target table meets the following conditions:  
  
-   The table is not being replicated.  
  
-   Table locking is specified (using TABLOCK). For table with clustered columnstore index, you don't need TABLOCK for minimal logging.  Additionally, only the data load into compressed rowgroups are minimally logged requiring a batchsize of 102400 or higher.  
  
    > [!NOTE]  
    >  Although data insertions are not logged in the transaction log during a minimally logged bulk-import operation, the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] still logs extent allocations each time a new extent is allocated to the table.  
  
-   Table is not a memory-optimized table.  
  
 Whether minimal logging can occur for a table also depends on whether the table is indexed and, if so, whether the table is empty:  
  
-   If the table has no indexes, data pages are minimally logged.  
  
-   If the table has no clustered index but has one or more nonclustered indexes, data pages are always minimally logged. How index pages are logged, however, depends on whether the table is empty:  
  
    -   If the table is empty, index pages are minimally logged.  
  
    -   If table is non-empty, index pages are fully logged.  
  
        > [!NOTE]  
        >  If you start with an empty table and bulk import the data in multiple batches, both index and data pages are minimally logged for the first batch, but beginning with the second batch, only data pages are minimally logged.  
  
-   If the table has a clustered index and is empty, both data and index pages are minimally logged. In contrast, if a table has a btree based  clustered index and is non-empty, data pages and index pages are both fully logged regardless of the recovery model. For tables with clustered columnstore index, the dataload into compressed rowgroup is always minimally logged independent of the table being empty or not when batchsize >= 102400.  
  
    > [!NOTE]  
    >  If you start with an empty table  rowstore table and bulk import the data in batches, both index and data pages are minimally logged for the first batch, but from the second batch onwards, only data pages are bulk logged.  
  
> [!NOTE]  
>  When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [View or Change the Recovery Model of a Database (SQL Server)](../../Topics/TopicNameContainA/View-or-Change-the-Recovery-Model-of-a-Database--SQL-Server-.md)  
  
   
  
## See Also  
 [Recovery Models (SQL Server)](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md)   
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)   
 [BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [Table Hints (Transact-SQL)](assetId:///8bf1316f-c0ef-49d0-90a7-3946bc8e7a89)   
 [INSERT (Transact-SQL)](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50)