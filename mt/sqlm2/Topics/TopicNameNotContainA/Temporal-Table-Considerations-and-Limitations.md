---
title: Temporal Table Considerations and Limitations
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8a21481-0f0e-41e3-a1ad-49a84091b422
---
# Temporal Table Considerations and Limitations
  There are some considerations and limitations to be aware of when working with temporal tables, due to the nature of system\-versioning.  
  
 Consider the following when working with temporal tables.  
  
-   A temporal table must have a primary key defined in order to correlate records between the current table and the history table, and the history table cannot have a primary key defined.  
  
-   The SYSTEM\_TIME period columns used to record the **SysStartTime** and **SysEndTime** values must be defined with a datatype of datetime2.  
  
-   If the name of a history table is specified during history table creation, you must specify the schema and table name.  
  
-   By default, the history table is **PAGE** compressed.  
  
-   If current table is partitioned, the history table is created on default file group because partitioning configuration is not replicated automatically from the current table to the history table.  
  
-   Temporal and history tables cannot be **FILETABLE** and can contain columns of any supported datatype other than **FILESTREAM** since **FILETABLE** and **FILESTREAM** allow data manipulation outside of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and thus system versioning cannot be guaranteed.  
  
-   While temporal tables support blob data types, such as **\(n\)varchar\(max\)**, **varbinary\(max\)**, **\(n\)text**, and **image**, their will incur significant storage costs and have performance implications due to their size. As such, when designing your system, care should be taken when using these data types.  
  
-   History table must be created in the same database as the current table. Temporal querying over **Linked Server** is not supported.  
  
-   History table cannot have constraints \(primary key, foreign key, table or column constraints\).  
  
-   Indexed views are not supported on top of temporal queries \(queries that use **FOR SYSTEM\_TIME** clause\)  
  
-   Online option \(**WITH \(ONLINE \= ON**\) has no effect on **ALTER TABLE ALTER COLUMN** in case of system\-versioned temporal table. ALTER column is not performed as online regardless of which value was specified for  ONLINE option.  
  
-   **INSERT** and **UPDATE** statements cannot reference the SYSTEM\_TIME period columns. Attempts to insert values directly into these columns will be blocked.  
  
-   **TRUNCATE TABLE** is not supported while **SYSTEM\_VERSIONING** is **ON**  
  
-   Direct modification of the data in a history table is not permitted.  
  
-   **ON DELETE CASCADE** and **ON UPDATE CASCADE** are not permitted on the current table. In other words, when temporal table is referencing table in the foreign key relationship \(corresponding to *parent\_object\_id* in sys.foreign\_keys\) CASCADE options are not allowed. To work around this limitation, use application logic or after triggers to maintain consistency on delete in primary key table \(corresponding to  *referenced\_object\_id* in sys.foreign\_keys\). If primary key table is temporal and referencing table is non\-temporal, there’s no such  limitation.  
  
-   **INSTEAD OF** triggers are not permitted on either the current or the history table to avoid invalidating the DML logic. **AFTER** triggers are permitted only on the current table. They are blocked on the history table to avoid invalidating the DML logic.  
  
-   Usage of replication technologies is limited.  
  
    -   **Always On:** Fully supported  
  
    -   **Change Data Capture and Change Data Tracking:** Supported only on the current table  
  
    -   **Snapshot and transactional replication**: Only supported for a single publisher without temporal being enabled and one subscriber with temporal enabled. In this case, the publisher is used for an OLTP workload while subscriber serves for offloading reporting \(including ‘AS OF’ querying\).    
        Use of multiple subscribers is not supported since this scenario may lead to inconsistent temporal data as each of them would depend on the local system clock.  
  
    -   **Merge replication:** Not supported for temporal tables  
  
-   Regular queries only affect data in the current table. To query data in the history table, you must use temporal queries. These are discussed later in this document in the section entitled Querying Temporal Data.  
  
-   An optimal indexing strategy will include a clustered columns store index and \/ or a B\-tree rowstore index on the current table and a clustered columnstore index on the history table for optimal storage size and performance. If you create \/ use your own history table, we strongly recommend that you create this type of index consisting of period columns starting with the end of period column to speed up temporal querying as well as speeding up the queries that are part of the data consistency check. The default history table has a clustered rowstore index created for you based on the period columns \(end, start\). At a minimum, a non\-clustered rowstore index is recommended.  
  
-   The following objects\/properties are not replicated from the current to the history table when the history table is created  
  
    -   Period definition  
  
    -   Identity definition  
  
    -   Indexes  
  
    -   Statistics  
  
    -   Check constraints  
  
    -   Triggers  
  
    -   Partitioning configuration  
  
    -   Permissions  
  
    -   Row\-level security predicates  
  
-   A history table cannot be configured as current table in a chain of history tables.  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Considerations%20and%20Limitations%20page)  
  
## See Also  
 [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md)   
 [Getting Started with System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Getting-Started-with-System-Versioned-Temporal-Tables.md)   
 [Temporal Table System Consistency Checks](../../Topics\TopicNameNotContainA/Temporal-Table-System-Consistency-Checks.md)   
 [Partitioning with Temporal Tables](../../Topics\TopicNameNotContainA/Partitioning-with-Temporal-Tables.md)   
 [Temporal Table Security](../../Topics\TopicNameNotContainA/Temporal-Table-Security.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Temporal Table Metadata Views and Functions](../../Topics\TopicNameNotContainA/Temporal-Table-Metadata-Views-and-Functions.md)  
  
  