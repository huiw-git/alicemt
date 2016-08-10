---
title: "Columnstore Indexes Versioned Feature Summary"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-indexes
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fe5ea05-5b19-45a4-9b7a-8ae5ca367897
caps.latest.revision: 27
manager: jhubbard
---
# Columnstore Indexes Versioned Feature Summary
Summary of columnstore features available for each version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and for the latest release of Azure SQL Database.  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] ([!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../Topics/TopicNameNotContainA/tokens/sqldbesa_md.md)] Premium Edition ([Preview in some regions](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag), [!INCLUDE[ssSDWfull](../../Topics/TopicNameNotContainA/tokens/ssSDWfull_md.md)]).|  
  
## Feature Summary for Product Releases  
 This table summarizes key features for columnstore indexes and the products in which they are available.  
  
|Columnstore Index Feature|[!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]|[!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]|[!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]|[!INCLUDE[sqldbesa](../../Topics/TopicNameNotContainA/tokens/sqldbesa_md.md)] Premium Edition|[!INCLUDE[ssSDW](../../Topics/TopicNameNotContainA/tokens/ssSDW_md.md)]|  
|-------------------------------|---------------------------|---------------------------|---------------------------|--------------------------------------------|-------------------------|  
|||||||  
|Batch execution for multi-threaded queries|yes|yes|yes|yes|yes|  
|Batch execution for single-threaded queries|||yes|yes|yes|  
|Archival compression option.||yes|yes|yes|yes|  
|Snapshot isolation and read-committed snapshot isolation|||yes|yes|yes|  
|Specify columnstore index when creating a table.|||yes|yes|yes|  
|AlwaysOn supports columnstore indexes.|yes|yes|yes|yes|yes|  
|AlwaysOn readable secondary supports read-only nonclustered columnstore index|yes|yes|yes|yes|yes|  
|AlwaysOn readable secondary supports updateable columnstore indexes.|||yes|||  
|Read-only nonclustered columnstore index on heap or btree.|yes|yes|yes*|yes*|yes*|  
|Updateable nonclustered columnstore index on heap or btree|||yes|yes|yes|  
|Additional btree indexes allowed on a heap or btree that has a nonclustered columnstore index.|yes|yes|yes|yes|yes|  
|Updateable clustered columnstore index.||yes|yes|yes|yes|  
|Btree index on a clustered columnstore index.|||yes|yes|yes|  
|Columnstore index on a memory-optimized table.|||yes|yes|yes|  
|Nonclustered columnstore index definition supports using a filtered condition.|||yes|yes|yes|  
|Compression delay option for columnstore indexes in CREATE TABLE and ALTER TABLE.|||yes|yes|yes|  
|||||||  
|||||||  
  
 *To create a readable nonclustered columnstore index, store the index on a read-only filegroup.  
  
## [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]  
 [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] adds key enhancements to improve the performance and flexibility of columnstore indexes. This enhances data warehousing scenarios and enables real-time operational analytics.  
  
### Functional  
  
-   A rowstore table can have one updateable nonclustered columnstore index. Previously, the nonclustered columnstore index was read-only.  
  
-   The nonclustered columnstore index definition supports using a filtered condition. Use this feature to create a nonclustered columnstore index on only the cold data of an operational workload. By doing this, the performance impact of having a columnstore index on an OLTP table will be minimal.  
  
-   An in-memory table can have one columnstore index. You can create it when the table is created or add it later with [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1). Previously, only a disk-based table could have a columnstore index.  
  
-   A clustered columnstore index can have one or more nonclustered rowstore indexes. Previously, the columnstore index did not support nonclustered indexes. SQL Server automatically maintains the nonclustered indexes for DML operations.  
  
-   Support for primary keys and foreign keys by using a btree index to enforce these constraints on a clustered columnstore index.  
  
-   Columnstore indexes have a compression delay option that minimizes the impact the transactional workload can have on real-time operational analytics.  This option allows for frequently changing rows to stabilize before compressing them into the columnstore. For details, see [CREATE COLUMNSTORE INDEX (Transact-SQL)](assetId:///7e1793b3-5383-4e3d-8cef-027c0c8cb5b1) and [Get started with Columnstore for real time operational analytics](../../Topics/TopicNameNotContainA/Get-started-with-Columnstore-for-real-time-operational-analytics.md).  
  
### Performance for database compatibility level 120 or 130  
  
-   Columnstore indexes support read committed snapshot isolation level (RCSI) and snapshot isolation (SI). This enables transactional consistent analytics queries with no locks.  
  
-   Columnstore supports index defragmentation by removing deleted rows without the need to explicitly rebuild the index. The ALTER INDEX … REORGANIZE statement will remove deleted rows, based on an internally defined policy, from the columnstore as an online operation  
  
-   Columnstore indexes can be access on an AlwaysOn readable secondary replica. You can improve performance for operational analytics by offloading analytics queries to an AlwaysOn secondary replica.  
  
-   To improve performance, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computes the aggregate functions MIN, MAX, SUM, COUNT, AVG during table scans when the data type uses no more than eight bytes, and is not of a string type. Aggregate pushdown is supported with or  without Group By clause for both clustered columnstore indexes and nonclustered columnstore indexes.  
  
-   Predicate pushdown speeds up queries that compare strings of type [v]char or n[v]char. This applies to the common comparison operators and includes operators such as LIKE that use bitmap filters. This works with all collations that SQL Server supports.  
  
### Performance for database compatibility level 130  
  
-   New batch mode execution support for queries using any of these operations:  
  
    -   SORT  
  
    -   Aggregates with multiple distinct functions. Some examples: COUNT/COUNT, AVG/SUM, CHECKSUM_AGG, STDEV/STDEVP.  
  
    -   Window aggregate functions: COUNT, COUNT_BIG, SUM, AVG, MIN, MAX, and CLR.  
  
    -   Window user-defined aggregates: CHECKSUM_AGG, STDEV, STDEVP, VAR, VARP, and GROUPING.  
  
    -   Window aggregate analytic functions:  LAG< LEAD, FIRST_VALUE, LAST_VALUE, PERCENTILE_CONT, PERCENTILE_DISC, CUME_DIST, and PERCENT_RANK.  
  
-   Single-threaded queries running under MAXDOP 1 or with a serial query plan execute in batch mode. Previously-only multi-threaded queries ran with batch execution.  
  
-   Memory optimized table queries can have parallel plans in SQL InterOp mode both when accessing data in rowstore or in columnstore index  
  
### Supportability  
 These system views are new for columnstore:  
  
-   [sys.column_store_row_groups (Transact-SQL)](assetId:///76e7fef2-d1a4-4272-a2bb-5f5dcd84aedc)  
  
-   [sys.dm_db_column_store_object_pool (Transact-SQL)](assetId:///a8a58ca7-0a7d-4786-bfd9-e8894bd345dd)  
  
-   [sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)](assetId:///31b71c68-50a0-4fd8-a7fe-2d2292be1163)  
  
-   [sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)](assetId:///f4c81104-7fe4-408f-9779-8808172dfdd2)  
  
-   [sys.dm_db_index_operational_stats (Transact-SQL)](assetId:///13adf2e5-2150-40a6-b346-e74a33ce29c6)  
  
-   [sys.dm_db_index_physical_stats (Transact-SQL)](assetId:///d294dd8e-82d5-4628-aa2d-e57702230613)  
  
-   [sys.internal_partitions (Transact-SQL)](assetId:///0262df2b-5ba7-4715-b17b-3d9ce470a38e)  
  
 These in-memory OLTP-based DMVs contain updates for columnstore:  
  
-   [sys.dm_db_xtp_hash_index_stats (Transact-SQL)](assetId:///45969884-cd61-48e8-aee5-c725c78e3e4c)  
  
-   [sys.dm_db_xtp_index_stats (Transact-SQL)](assetId:///8d0a50b8-2015-4576-930f-e3307dfc888e)  
  
-   [sys.dm_db_xtp_memory_consumers (Transact-SQL)](assetId:///f7ab2eaf-e627-464d-91fe-0e170b3f37bc)  
  
-   [sys.dm_db_xtp_nonclustered_index_stats (Transact-SQL)](assetId:///d55ba31c-296c-419b-9c4b-c126e0a3d156)  
  
-   [sys.dm_db_xtp_object_stats (Transact-SQL)](assetId:///07300b59-3cab-4d3e-8138-5ea8f584f88f)  
  
-   [sys.dm_db_xtp_table_memory_stats (Transact-SQL)](assetId:///ad0efc06-3d9c-4861-9dfa-a7a87822d0c8)  
  
### Limitations  
  
-   MERGE is disabled when a btree index is defined on a clustered columnstore index.  
  
-   For in-memory tables, a columnstore index must include all the columns; the columnstore index cannot have a filtered condition.  
  
-   For in-memory tables, queries on columnstore indexes run only in InterOP mode, and not in the in-memory native mode. Parallel execution is supported.  
  
## SQL Server 2014  
 SQL Server 2014 introduced the clustered column store index as the primary storage format. This allowed regular loads as well as update, delete, and insert operations.  
  
-   The table can use a clustered column store index as the primary table storage. No other indexes are allowed on the table, but the clustered column store index is updateable so you can perform regular loads and make changes to individual rows.  
  
-   The nonclustered column store index continues to have the same functionality as in SQL Server 2012 except for additional operators that can now be executed in batch mode. It is still not updateable except by rebuilding, and by using partition switching. The nonclustered columnstore index is supported on disk-based tables only, and not on in-memory tables.  
  
-   The clustered and nonclustered column store index has an archival compression option that further compresses the data. The archival option is useful for reducing the data size both in memory and on disk, but does slow query performance. It works well for data that is accessed infrequently.  
  
-   The clustered columnstore index and the nonclustered columnstore index function in a very similar way; they use the same columnar storage format, same query processing engine, and the same set of dynamic management views. The difference is primary versus secondary index types, and the nonclustered columnstore index is read-only.  
  
-   These operators run in batch mode for multi-threaded queries: scan, filter, project, join, group by, and union all.  
  
## SQL Server 2012  
 SQL Server 2012 introduced the nonclustered columnstore index as another index type on rowstore tables and batch processing for queries on columnstore data.  
  
-   A rowstore table can have one nonclustered columnstore index.  
  
-   The colum store index is read-only. After you create the columnstore index, you cannot update the table by insert, delete, and update operations; to perform these operations you must drop the index, update the table and rebuild the columnstore index. You can load additional data into the table by using partition switching. The advantage of partition switching is you can load data without dropping and rebuilding the columnstore index.  
  
-   The column store index always requires extra storage, typically an additional 10% over rowstore, because it stores a copy of the data.  
  
-   Batch processing providex 2x or better query performance, but it is only available for parallel query execution.  
  
## See Also  
 [Columnstore Indexes Guide](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Guide.md)   
 [Columnstore Indexes Data Loading](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Data-Loading.md)   
 [Columnstore Indexes Query Performance](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Query-Performance.md)   
 [Get started with Columnstore for real time operational analytics](../../Topics/TopicNameNotContainA/Get-started-with-Columnstore-for-real-time-operational-analytics.md)   
 [Columnstore Indexes for Data Warehousing](../../Topics/TopicNameNotContainA/Columnstore-Indexes-for-Data-Warehousing.md)   
 [Columnstore Indexes Defragmentation](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Defragmentation.md)