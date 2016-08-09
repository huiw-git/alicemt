---
title: "What&#39;s New in Database Engine"
ms.custom: 
  - SQL2016_New_Updated
  - SQL2016_rc1
ms.date: 2016-05-26
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
caps.latest.revision: 410
caps.handback.revision: 0
manager: jhubbard
---
# What&#39;s New in Database Engine
This topic summarizes the enhancements introduced in the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] release of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)].  The new features and enhancements increase the power and productivity of architects, developers, and administrators who design, develop, and maintain data storage systems.  
  
 To review what is new in the other SQL Server components, see [What's New in SQL Server 2016](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] is a 64-bit application. 32-bit installation is discontinued, though some elements run as 32-bit components.  
  
 **Try it out :**  
  
-   To download [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], go to  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**![download](../../Topics/TopicNameNotContainA/images/download.png "download").  
  
-   Have an Azure account?  Then go **[Here](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rc0evaluationwindowsserver2012r2/?wt.mc_id=sqL16_vm)** to spin up a Virtual Machine with [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] already installed.  
  
 ![note](../../Topics/TopicNameNotContainA/images/ssrs_fyi_note.png "ssrs_fyi_note") For the current release notes, see [SQL Server 2016 Release Notes](../../Topics/TopicNameNotContainA/SQL-Server-2016-Release-Notes.md).  
  
##  <a name="Feature"></a> Database Engine Feature Enhancements  
  
###  <a name="columnstore"></a> Columnstore Indexes  
 **[CTP 3.0]** This release has supportability and performance improvements.  
  
-   A read-only nonclustered columnstore index is updateable after upgrade.  A rebuild of the index is not required to make it updateable.  
  
-   There are performance improvements for analytics queries on columnstore indexes,  especially for aggregates and string predicates.  
  
-   DMVs and XEvents have supportability improvements.  
  
 For more details, see these topics in the [Columnstore Indexes Guide](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Guide.md) section of Books Online:  
  
-   [Columnstore Indexes Versioned Feature Summary](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Versioned-Feature-Summary.md) –includes what’s new  
  
-   [Columnstore Indexes Data Loading](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Data-Loading.md)  
  
-   [Columnstore Indexes Query Performance](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Query-Performance.md)  
  
-   [Get started with Columnstore for real time operational analytics](../../Topics/TopicNameNotContainA/Get-started-with-Columnstore-for-real-time-operational-analytics.md)  
  
-   [Columnstore Indexes for Data Warehousing](../../Topics/TopicNameNotContainA/Columnstore-Indexes-for-Data-Warehousing.md)  
  
-   [Columnstore Indexes Defragmentation](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Defragmentation.md)  
  
 **[CTP 2.0]** This release offers several new improvements for columnstore indexes including updateable nonclustered columnstore indexes, columnstore indexes on in-memory tables, and many more new features for operational analytics.  
  
###  <a name="scopedconfiguration"></a> Database Scoped Configurations  
 **[RC0]**  
  
 This release  now supports a new database level object that holds optional configuration values that affect the behavior of the application code at the database level. This support is available in both [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] and [!INCLUDE[sqldbesa](../../Topics/TopicNameNotContainA/tokens/sqldbesa_md.md)] using  the new [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a) statement. This  statement modifies the default [!INCLUDE[ssDECurrent](../../Topics/TopicNameNotContainA/tokens/ssDECurrent_md.md)] behavior for a particular database. A generic mechanism for creating database configuration(s) at creation time is not provided.  
  
 These options are:  
  
-   Clear procedure cache.  
  
-   Set the MAXDOP parameter to an arbitrary value (1,2, ...) for the primary database based on what works best for that particular database and set a different value (e.g. 0) for all secondary database used (e.g. for reporting queries).  
  
-   Set the query optimizer cardinality estimation model independent of the database to compatibility level.  
  
-   Enable or disable parameter sniffing at the database level.  
  
-   Enable or disable query optimization hotfixes at the database level.  
  
###  <a name="InMemory"></a> In-Memory OLTP  
 **[RC0]**  
  
 **Parallel scan of nonclustered indexes:**  
  
 All indexes on memory-optimized tables now support parallel scan. This increases the performance of analytical queries that scan large sets of data.  
  
 **Reduced downtime during upgrade:**  
  
 Upgrade from an earlier build of SQL Server, to SQL Server 2016, no longer runs database recovery. Therefore data size no longer affects the duration of upgrade. For upgrade and attach/restore from SQL Server 2014, the database is restarted only once.  
  
 **@@spid:**  
  
 The built-in configuration function @@SPID is now supported in the following:  
  
-   Natively compiled T-SQL modules.  
  
-   Constraints on memory-optimized tables.  
  
 **Log-optimized and parallel ALTER TABLE:**  
  
 Most ALTER TABLE scenarios now run in parallel and result in an optimization of writes to the transaction log. The optimization is that only the metadata changes are written to the transaction log. However, the following ALTER TABLE operations run single-threaded and are not log-optimized.  
  
 The single-threaded operations require that the entire contents of the altered table be written to the log. A list of single-threaded operations follows:  
  
-   Alter or add a column to use a large object (LOB) type: nvarchar(max), varchar(max), or varbinary(max).  
  
-   Add or drop a COLUMNSTORE index.  
  
-   Almost anything that affects an off-row column.  
    An off-row column does not fit in the 8060 byte row, and is one of the following data types: char or nchar, varchar or nvarchar, binary or varbinary.  
  
    -   Cause an on-row column to move off-row.  
  
    -   Cause an off-row column to move on-row.  
  
    -   Create a new off-row column.  
  
    -   The exception is lengthening an already off-row column. For this the log writes are optimized.  
  
     The longest columns are stored off-row. But all index key columns must be stored in-row.  
  
-   The following query shows all columns that are stored off-row, along with their sizes. A size of -1 indicates a LOB column. All LOB columns are stored off-row.  
  
    ```tsql  
    SELECT  
          OBJECT_NAME(m.object_id) as [table],  
          c.name                   as [column],  
          c.max_length  
       FROM  
               sys.memory_optimized_tables_internal_attributes as m  
          JOIN sys.columns                                     as c  
                            on m.object_id = c.object_id  
                           and m.minor_id  = c.column_id  
       WHERE  
          m.type = 5;  
    ```  
  
 **[CTP 3.3]**  
  
 **Statistics:**  
  
 Statistics for memory-optimized tables are now updated automatically. In addition, sampling is now a supported method to collect statistics, allowing you to avoid the more expensive fullscan method.  
  
-   To enable automatically updated and sampled statistics, ensure your database is set to [compatibility level](assetId:///ca5fd220-d5ea-4182-8950-55d4101a86f6) = 130.  
  
-   To enable pre-existing statistics to be updated automatically, a one-time manual update operation is required (see example *One-time script for statistics*, shortly below).  
  
-   The recompilation of natively compiled modules is still manual. Use [sp_recompile](assetId:///6192ca87-febd-4075-8199-14b4fa609b8c) to recompile natively compiled modules.  
  
 *One-time script for statistics:* On your CTP3.3 installation, for memory-optimized tables that were created before CTP3.3, you can run the following Transact-SQL script one time to update the statistics of memory-optimized tables. Statistics are gathered by data sampling rather than a more resource intensive full scan. The run also enables the automatic update of statistics from then onward (assuming [AUTO_UPDATE_STATISTICS](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) is enabled for the database).  
  
```tsql  
-- Assuming AUTO_UPDATE_STATISTICS is already ON for your database:  
-- ALTER DATABASE CURRENT SET AUTO_UPDATE_STATISTICS ON;  
GO  
  
ALTER DATABASE CURRENT SET COMPATIBILITY_LEVEL = 130;  
GO  
  
DECLARE @sql NVARCHAR(MAX) = N'';  
  
SELECT  
      @sql += N'UPDATE STATISTICS '  
         + quotename(schema_name(t.schema_id))  
         + N'.'  
         + quotename(t.name)  
         + ';' + CHAR(13) + CHAR(10)   
   FROM sys.tables AS t  
   WHERE t.is_memory_optimized = 1  
;  
  
EXECUTE sp_executesql @sql;  
GO  
  
-- Each row appended to @sql looks roughly like:  
-- UPDATE STATISTICS [dbo].[MyMemoryOptimizedTable];  
```  
  
 **Parallel scan for memory-optimized tables:**  
  
 Memory-optimized tables are now scanned in parallel. This improves the performance of analytical queries.  
  
 Reminders:  
  
-   Support for the parallel scan of hash indexes has been supported since CTP2.0.  
  
-   Support for the parallel scan of columnstore indexes has been supported since columnstore indexes first became available.  
  
-   Support for the parallel scan of regular harddrive-based tables and indexes has been supported for years.  
  
 **LOBs with large row size for a memory-optimized table:**  
  
 Large object (LOB) types include varchar(max) and nvarchar(max) and varbinary(max). You can now have a memory-optimized table with a row size > 8060 bytes, even when no column in the table is a LOB type. CTPs 3.1 and 3.2 provided this support only when LOB type columns caused the row size to be > 8060 bytes.  
  
 The following T-SQL script illustrates a table with multiple non-LOB columns, named C1-C4, whose combined sizes are > 8060 bytes:  
  
```tsql  
CREATE TABLE dbo.LargeTableSample  
(  
      Id   int   IDENTITY   PRIMARY KEY NONCLUSTERED,  
      C1   nvarchar(4000),  
      C2   nvarchar(4000),  
      C3   nvarchar(4000),  
      C4   nvarchar(4000),  
      Misc nvarchar(max)  
) WITH (MEMORY_OPTIMIZED = ON);  
GO  
```  
  
 **LOBs with native compilation:**  
  
 Now when you use a built-in string function in a natively compiled module, the function can accept as an argument the LOB types of varchar(max) or nvarchar(max) or varbinary(max). The built-in string functions include '+', Len, LTrim, RTrim, and Substring. Also, these LOB types can be the return type from a natively compiled scalar UDF (user-defined function), as shown in the following T-SQL script:  
  
```tsql  
CREATE FUNCTION dbo.TRIM_CONCAT  
(  
   @p1 nvarchar(max),  
   @p2 nvarchar(max)  
)  
RETURNS nvarchar(max)  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS  
BEGIN ATOMIC WITH  
      (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch')  
   RETURN RTRIM(@p1) + LTRIM(@p2);  
END  
GO  
```  
  
 **OUTPUT clause in natively compiled stored procedures:**  
  
 In a natively compiled stored procedure, INSERT and UPDATE and DELETE statements can now include the [OUTPUT clause](assetId:///41b9962c-0c71-4227-80a0-08fdc19f5fe4).  
  
 **[CTP 3.2]**  
  
 In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], enhancements to [In-Memory OLTP](../../Topics/TopicNameNotContainA/In-Memory-OLTP--In-Memory-Optimization-.md) make adopting the feature to achieve performance benefits easier, in new as well as existing applications.   Scaling improvements allow putting more data in memory-optimized tables and achieve higher throughput in order to support bigger workloads.  
  
 **[CTP3.1]**  
  
 **Transact-SQL Improvements:**  
  
-   [Support in natively compiled modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#qsancsp) for:  
  
     LOB types [varchar(max), nvarchar(max), and varbinary(max)] for parameters and variables. This build does not yet support string functions len, rtrim, lrtrim, and substring with  LOB types in natively compiled modules.  
  
-   Support with memory-optimized tables for:  
  
     NULLable index key columns. It is now allowed to include NULLable columns in the keys of indexes on memory-optimized tables.  
  
     LOB types [varchar(max), nvarchar(max), and varbinary(max)] can  be used with columns in memory-optimized tables  
  
     UNIQUE indexes in memory-optimized tables. Indexes can now be specified as UNIQUE  
  
 **[CTP 3.0]**  
  
 **Transact-SQL Improvements:**  
  
-   [Support in natively compiled modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#qsancsp) for:  
  
     Natively compiled inline table-valued functions (TVFs)  
  
     EXECUTE AS CALLER support - the EXECUTE AS clause is no longer required for native modules  
  
     Built-in  security functions and increased support for built-in math functions  
  
-   Support with memory-optimized tables for:  
  
     FOREIGN KEY constraints between memory-optimized tables. At this point, foreign key references must reference a primary key.  
  
     CHECK constraints  
  
     UNIQUE constraints  
  
     Triggers (AFTER) for INSERT/UPDATE/DELETE operations. Triggers on memory-optimized tables are natively compiled, and thus use WITH NATIVE_COMPILATION.  
  
 **Cross-feature support:**  
  
-   Support for using temporal system-versioning with In-Memory OLTP. For more information, see [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics/TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)  
  
-   Query store support for natively compiled code from In-Memory OLTP workloads. For more information, see [Using the Query Store with In-Memory OLTP](../../Topics/TopicNameNotContainA/Using-the-Query-Store-with-In-Memory-OLTP.md).  
  
-   [Row-Level Security in Memory-Optimized Tables](../../Topics/TopicNameNotContainA/Introduction-to-Memory-Optimized-Tables.md#rls)  
  
 **[CTP 2.0]**  
  
 **Transact-SQL Improvements:**  
  
-   [Support in natively compiled modules](../../Topics/TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md#qsancsp) for:  
  
     Disjunction (OR, NOT)  
  
     UNION and UNION ALL  
  
     SELECT DISTINCT  
  
     OUTER JOIN  
  
     Subqueries in SELECT statements (EXISTS, IN, scalar subqueries)  
  
     Nested execution (EXECUTE) of natively compiled modules  
  
-   [Altering Natively Compiled T-SQL Modules](../../Topics/TopicNameNotContainA/Altering-Natively-Compiled-T-SQL-Modules.md) support for natively compiled procedures, functions, and triggers  
  
-   [Altering Memory-Optimized Tables](../../Topics/TopicNameNotContainA/Altering-Memory-Optimized-Tables.md) support for schema and index changes  
  
     The new ALTER TABLE ... ADD/DROP/ALTER INDEX syntax is introduced for index changes on memory-optimized tables  
  
-   Full support for all [Collation and Unicode Support](../../Topics/TopicNameNotContainA/Collation-and-Unicode-Support.md)  
  
     (var)char columns can use any code page supported by SQL Server  
  
     Character columns  in index keys can use any SQL Server collation  
  
     Expressions in natively compiled modules as well as constraints on memory-optimized tables can use any SQL Server collation  
  
-   [Scalar User-Defined Functions for In-Memory OLTP](../../Topics/TopicNameNotContainA/Scalar-User-Defined-Functions-for-In-Memory-OLTP.md)  
  
 **Performance and Scaling improvements:**  
  
-   Increased data size: a database can now have up to 2 terabytes of user data in memory-optimized tables with SCHEMA_AND_DATA  
  
-   [Scalability](../../Topics/TopicNameNotContainA/Scalability.md) improvements in the persistence layer  
  
-   Parallel plan support for [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](../../Topics/TopicNameNotContainA/Accessing-Memory-Optimized-Tables-Using-Interpreted-Transact-SQL.md)  
  
-   Parallel scan support for HASH indexes  
  
 **Enhancements in SQL Server Management Studio:**  
  
-   The [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](../../Topics/TopicNameContainA/Determining-if-a-Table-or-Stored-Procedure-Should-Be-Ported-to-In-Memory-OLTP.md) no longer requires the configuration of data collectors or management data warehouse. The report can now run directly on a production database.  
  
-   [PowerShell Cmdlet for Migration Evaluation](../../Topics/TopicNameNotContainA/PowerShell-Cmdlet-for-Migration-Evaluation.md) for evaluating the migration fitness of multiple objects in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database.  
  
-   Generate migration checklists by right-clicking on a database, and selecting Tasks -> Generate In-Memory OLTP migration checklists  
  
 **Cross-feature support:**  
  
-   [MARS (Multiple Active Result Set)](assetId:///ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83) connections  can now access memory-optimized tables and natively compiled stored procedures  
  
-   Transparent Data Encryption support. If a database is configured for ENCRYPTION, files in the MEMORY_OPTIMIZED_DATA filegroup are now also encrypted.  
  
 For more information, see [In-Memory OLTP (In-Memory Optimization)](../../Topics/TopicNameNotContainA/In-Memory-OLTP--In-Memory-Optimization-.md).  
  
###  <a name="LiveStats"></a> Live Query Statistics  
 **[CTP 2.0]** [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] provides the ability to view the live execution plan of an active query. This live query plan provides real-time insights into the query execution process as the controls flow from one query plan operator to another. For more information, see [Live Query Statistics](../../Topics/TopicNameNotContainA/Live-Query-Statistics.md).  
  
###  <a name="QueryStore"></a> Query Store  
 **[CTP 2.0]** Query store is a new feature that provides DBAs with insight on query plan choice and performance. It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans. The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review. It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server. The query store presents information by using a [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] dialog box, and lets you force the query to one of the selected query plans. For more information, see [Monitoring Performance By Using the Query Store](../../Topics/TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md).  
  
 **[CTP 3.0]** Removing some restrictions for Query Store including adding support for performance monitoring supported for natively compiled code from In-Memory OLTP workloads. For more information, see [Using the Query Store with In-Memory OLTP](../../Topics/TopicNameNotContainA/Using-the-Query-Store-with-In-Memory-OLTP.md).  
  
-   Stored plan is semantically equivalent to one that is produced when SET SHOWPLAN_XML is set to ON with one difference: plans in Query Store are always split and stored per individual statement.  
  
-   Runtime statistics collection is controlled with **sys.sp_xtp_control_query_exec_stats** and is not enabled by default.  
  
-   **is_natively_compiled** field added to **sys.query_store_plan** to help finding queries  generated by the native code compilation.  
  
-   Plan forcing for queries from natively compiled modules is available and forced plans are honored during module recompilation. For disk-based workloads, Query Store does not guarantee success of plan forcing operation as some plan shapes cannot be forced.  
  
-   Memory grants metrics within **sys.query_store_runtime_stats** are not populated for natively compiled queries; their values are always 0.  
  
 Improving implementation of time-based cleanup (configured with **STALE_QUERY_THRESHOLD_DAYS**) to run in multiple transactions, holding database lock for a shorter period of time and thus minimize impact on customer workload.  
  
 [Top](#Top)  
  
###  <a name="TT"></a> Temporal Tables  
 **[CTP 3.0]**In CTP 3.0, temporal tables have been enhanced as follows:  
  
-   Support for using temporal system-versioning with In-Memory OLTP. For more information, see [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics/TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)  
  
-   Direct ALTER for system-versioned temporal tables enables modifying table schema without introducing maintenance windows. Columns can be added, altered or dropped while **SYSTEM_VERSIONING** is **ON**, including support for adding or removing the **HIDDEN** property to or from a period column.  
  
-   Support for temporal querying clause **FOR SYSTEM_TIME ALL** that enables users to query entire data history easily without specifying period boundaries  
  
-   Optimized CONTAINED IN implementation with minimized locking on current table. This optimizes analysis queries on historical data.  
  
 **[CTP 2.3]**You can mark one or both period columns with the *HIDDEN* flag so that these columns will not appear in query results unless a period column is expressly specified in the query.  
  
 **[CTP 2.0]** A temporal table is a new type of table that provides correct information about stored facts at any point in time. Each temporal table consists of two tables actually, one for the current data and one for the historical data. The system ensures that when the data changes in the table with the current data the previous values are stored in the historical table. Querying constructs are provided to hide this complexity from users. For more information, see [Temporal Tables](../../Topics/TopicNameNotContainA/Temporal-Tables.md).  
  
###  <a name="StripedBackupToAzure"></a> Striped Backups to Microsoft Azure Blob Storage  
 **[CTP 2.0]** SQL Server backup to URL using the Microsoft Azure Blob storage service now supports using block blobs instead of page blobs. Block blobs have a size limitation of 200GB per blob, whereas page blobs have a size limitation per blob of 1 TB. With block blobs, you can stripe your backup set across multiple blobs resulting in a maximum backup size is 12.8 TB. Backup to page blobs does not support striping. In addition, block blobs have superior performance and a lower cost. As a result, striped backups for large databases can experience significantly decreased backup and restore times from Microsoft Azure.  
  
 There are two steps required to stripe your backup set to block blobs. First, you must obtain a [Shared Access Signature (SAS)](http://azure.microsoft.com/documentation/articles/storage-dotnet-shared-access-signature-part-1/) token to a container in your Azure Storage account. This SAS token is used to create a SQL Credential and then this SAS token is used when the Azure container is specified as the backup device. One way to obtain this SAS token is to use Azure PowerShell commands. Then you use the same Transact-SQL or PowerShell backup commands without specifying the `WITH CREDENTIAL` clause that was formerly required when using backup to URL. For examples, see [Code Examples](../../Topics/TopicNameNotContainA/SQL-Server-Backup-to-URL.md#Examples).  
  
> [!NOTE]  
>  For [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], the new backup to URL functionality does not yet have corresponding UI support in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
###  <a name="FileSnapshotBackup"></a> File-Snapshot Backups to Microsoft Azure Blob Storage  
 **[CTP 2.0]** SQL Server backup to URL now supports using Azure snapshots to backup databases in which all database files are stored using the Microsoft Azure Blob storage service. For more information, see [File-Snapshot Backups for Database Files in Azure](../../Topics/TopicNameNotContainA/File-Snapshot-Backups-for-Database-Files-in-Azure.md).  
  
###  <a name="ManagedBackup"></a> Managed Backup  
 **[CTP 2.0]** In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] SQL Server Managed Backup to Microsoft Azure uses the new block blob storage for backup files. There are also several changes and enhancements to Managed Backup.  
  
-   Support for both automated and custom scheduling of backups.  
  
-   Support backups for system databases.  
  
-   Support for databases that are using the Simple recovery model.  
  
 For more information, see [SQL Server Managed Backup to Microsoft Azure](../../Topics/TopicNameNotContainA/SQL-Server-Managed-Backup-to-Microsoft-Azure.md)  
  
> [!NOTE]  
>  For [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], these new managed backup features do not yet have corresponding UI support in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
###  <a name="TraceFlag"></a> Trace flag 4199 behaviors are enabled  
 **[CTP 2.0]** In general, you do not need to use trace flag 4199 in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] since *most* of the query optimizer behaviors controlled by this trace flag are enabled unconditionally under the latest compativility level (130) in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)].  
  
 [Top](#Top)  
  
###  <a name="multipleTempDB"></a> TempDB Database  
 There are several enhancements to TempDB:  
  
-   Trace Flags 1117 and 1118 are not required for tempdb anymore. If there are multiple tempdb database files all files will grow at the same time depending on growth settings. In addition, all allocations in tempdb will use uniform extents.  
  
-   By default, setup adds as many tempdb files as the CPU count or 8, whichever is lower.  
  
-   During setup, you can configure the number of tempdb database files, initial size, autogrowth and directory placement using the new UI input control on the Database Engine Configuration - TempDB section of SQL Server Installation Wizard.  
  
-   The default initial size is 8MB and the default autogrowth is 64MB.  
  
-   You can specify multiple volumes for tempdb database files. If multiple directories are specified tempdb data files will be spread across the directories in a round-robin fashion.  
  
###  <a name="ForJson"></a> Built-in JSON Support  
 **[CTP 2.0]** Format query results as JSON by adding the **FOR JSON** clause to a **SELECT** statement. Use the **FOR JSON** clause, for example, to delegate the formatting of JSON output from your client applications to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Here's a sample query that uses the **FOR JSON** clause.  
  
 **Query**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Results**  
  
```json  
[   
   { "name": "John" },  
   { "name": "Jane", "surname": "Doe" }  
]  
  
```  
  
 For more info, see [Format Query Results as JSON with FOR JSON (SQL Server)](../../Topics/TopicNameNotContainA/Format-Query-Results-as-JSON-with-FOR-JSON--SQL-Server-.md).  
  
 **[CTP 3.0]** Convert JSON data to rows and columns by calling the **OPENJSON** rowset provider function. Use **OPENJSON** to import JSON data into SQL Server, or convert JSON data to rows and columns for an app or service that can't currently consume JSON directly. Here's an example that uses **OPENJSON** with the default schema.  
  
 **Query**  
  
```tsql  
SELECT * FROM OPENJSON('{"name":"John","surname":"Doe","age":45}')  
```  
  
 **Results**  
  
|Key|Value|  
|---------|-----------|  
|name|John|  
|surname|Doe|  
|age|45|  
  
 For more info, see [Convert JSON Data to Rows and Columns with OPENJSON (SQL Server)](../../Topics/TopicNameNotContainA/Convert-JSON-Data-to-Rows-and-Columns-with-OPENJSON--SQL-Server-.md).  
  
 **[CTP 3.0]** The built-in support for JSON also now includes the following built-in functions.  
  
-   **ISJSON** tests whether a string contains valid JSON. For more info, see [ISJSON (Transact-SQL)](assetId:///c836f3d3-3e17-44ae-92bf-f341918896c3)  
  
-   **JSON_VALUE** extracts a scalar value from a JSON string.For more info, see [JSON_VALUE (Transact-SQL)](assetId:///cd016e14-11eb-4eaf-bf05-c7cfcc820a10).  
  
-   **JSON_QUERY** extracts an object or an array from a JSON string. For more info, see [JSON_QUERY (Transact-SQL)](assetId:///1ab0d90f-19b6-4988-ab4f-22fdf28b7c79).  
  
 For more info, see [Validate, Query, and Change JSON Data with Built-in Functions (SQL Server)](../../Topics/TopicNameNotContainA/Validate--Query--and-Change-JSON-Data-with-Built-in-Functions--SQL-Server-.md).  
  
 **[CTP 3.0] Test drive built-in JSON support with the AdventureWorks sample database.** To get the AdventureWorks sample database, download at least the database file and the samples and scripts file from [here](https://www.microsoft.com/en-us/download/details.aspx?id=49502). After you restore the sample database to an instance of SQL Server 2016, unzip the samples file and open the "JSON Sample Queries procedures views and indexes.sql" file from the JSON folder. Run the scripts in this file to reformat some existing data as JSON data, run sample queries and reports over the JSON data, index the JSON data, and import and export JSON.  
  
 **[CTP 3.2]** To remove the square brackets that surround the JSON output of the **FOR JSON** clause by default, specify the **WITHOUT_ARRAY_WRAPPER** option. Use this option to generate a single JSON object as output.  If you don't specify this option, the JSON output is enclosed within square brackets.  
  
 The following example shows the output of the **FOR JSON** clause with and without the **WITHOUT_ARRAY_WRAPPER** option.  
  
 **Query**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **Result** With the **WITHOUT_ARRAY_WRAPPER** option  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **Result** Without the **WITHOUT_ARRAY_WRAPPER** option  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 For more info, see [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option (SQL Server)](../../Topics/TopicNameNotContainA/Remove-Square-Brackets-from-JSON-Output-with-the-WITHOUT_ARRAY_WRAPPER-Option--SQL-Server-.md).  
  
 **[RC0]** The built-in support for JSON also now includes the [JSON_MODIFY (Transact-SQL)](assetId:///96bc8255-a037-4907-aec4-1a9c30814651) function. Use the **JSON_MODIFY**  function to update the value of a property in a JSON string and return the updated JSON string.  
  
###  <a name="bkPolyBase"></a> PolyBase  
 PolyBase allows you to use T-SQL statements to access data stored in Hadoop or Azure Blob Storage and query it in an adhoc fashion. It also lets you query semi-structured data and join the results with relational data sets stored in SQL Server. PolyBase is optimized for data warehousing workloads and intended for analytical query scenarios.  
  
 For more information, see [PolyBase Guide](../../Topics/TopicNameNotContainA/PolyBase-Guide.md).  
  
 **[CTP 2.4]**  
  
 The PolyBase feature supports all SQL Server collations.  
  
 **[CTP 3.0]**  
  
-   PolyBase query performance improved with scale-out computation on external data (PolyBase scale-out groups).  
  
-   PolyBase query performance improved with faster data movement from HDFS to SQL Server and between PolyBase Engine and SQL Server.  
  
-   Export data to external data source using `INSERT INTO EXTERNAL TABLE SELECT FROM TABLE`.  
  
-   Support added for push-down computation to Hadoop for string operations (compare, LIKE).  
  
-   Added support for **ALTER EXTERNAL DATA SOURCE** statement.  
  
 **[CTP 3.2]**  
  
-   Support added for Parquet file formats.  
  
 **[CTP 3.3]**  
  
-   Support added for Hortonworks HDP2.3 version Hadoop clusters.  
  
 **[RC 0]**  
  
-   Added support for the latest Cloudera distribution CDH5.5 on Linux.  
  
-   Added support for public containers and blobs in Azure blob storage.  
  
###  <a name="stretch"></a> Stretch Database  
 **[CTP 2.0]** Stretch Database is a new feature in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] that leverages resources in Windows Azure to store and query archival data. Stretch Database automatically archives eligible rows from Stretch-enabled tables and uses computational resources in Azure to offload queries over the archived rows. For more info, see [Stretch Database](../../Topics/TopicNameNotContainA/Stretch-Database.md).  
  
 **[CTP 2.2]** Stretch Database now includes the following features and enhancements.  
  
-   You can now add security policies to a table that has been configured for Stretch Database. You can also configure a table that uses Row-Level Security for Stretch Database.  
  
-   Stretch Database Advisor is now available as a component of SQL Server 2016 Upgrade Advisor Preview 1. You can download Upgrade Advisor Preview 1  [here](https://www.microsoft.com/en-us/download/details.aspx?id=48119) or you can install it by using the Web Platform Installer.   
    Stretch Database Advisor helps you to adopt Stretch Database by analyzing existing database tables based on adjustable table size thresholds to identify candidates for Stretch Database. For more info, see [Identify databases and tables for Stretch Database by running Stretch Database Advisor](../../Topics/TopicNameNotContainA/Identify-databases-and-tables-for-Stretch-Database-by-running-Stretch-Database-Advisor.md).  
  
 **[CTP 3.0]** Stretch Database now includes the following features and enhancements.  
  
-   **In SQL Server Management Studio**  
  
    -   New context menu options on databases and tables reflect new Stretch Database functionality.  
  
    -   You can enable Stretch Database for individual tables.  
  
    -   You can pause or disable data migration at the table level.  
  
    -   The visual Stretch Database Monitor lets you monitor the current status of data migration, including the ability to pause the migration at the table level.  
  
-   **In the Enable Stretch Database Wizard**  
  
    -   The updated and simplified Wizard reduces the number of steps required to enable or reconfigure Stretch  
        Database.  
  
    -   The Wizard enables Stretch Database for you at the server level, if you have administrator rights.  
  
    -   You can create a new Azure SQL Database server or use an existing SQL Database server to store the remote data.  
  
    -   When you're selecting tables, the Wizard now provides better validation, warning, and error messages.  
  
-   **Other**  
  
    -   Stretch Database now uses database scoped credentials. This improves support for Always On availability groups.  
  
    -   To improve support for AlwaysEncrypted, you can now enable Stretch Database on a table with columns that are using AlwaysEncrypted.  
  
    -   Joins between tables that are configured for Stretch perform better.  
  
-   **Test drive Stretch Database with the AdventureWorks sample database.** To get the AdventureWorks sample database, download at least the database file and the samples and scripts file from [here](https://www.microsoft.com/en-us/download/details.aspx?id=49502). After you restore the sample database to an instance of SQL Server 2016, unzip the samples file and open the Stretch DB Samples file from the Stretch DB folder. Run the scripts in this file to check the space used by your data before and after you enable Stretch Database,  to track the progress of data migration, and to confirm that you can continue to query existing data and insert new data both during and after data migration.  
  
 **[CTP 3.1]** Stretch Database now includes the following features and enhancements.  
  
-   You can now specify a predicate to select rows to archive from a table that contains both historical and current data. The predicate must call an inline table-valued function. In CTP 3.1 and 3.2, this option is not available in the wizard. You have to use the ALTER TABLE statement to configure Stretch Database with this option. In CTP 3.1 and 3.2, this feature also requires a trace flag. For more info, see [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md), [Select rows to migrate by using a filter predicate (Stretch Database)](../../Topics/TopicNameContainA/Select-rows-to-migrate-by-using-a-filter-predicate--Stretch-Database-.md), and [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1).  
  
     If you don't specify a filter predicate, the entire table is archived.  
  
-   Stretch Database is now compatible with temporal tables.  
  
    -   You can enable Stretch on the history table that's already associated with a temporal table.  
  
    -   You can also configure a table that's already enabled for Stretch as the history table for a temporal table.  
  
     For more info about using Stretch Database with temporal tables, see [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics/TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md).  
  
-   You can now unmigrate the data that Stretch Database has migrated to Azure. In CTP 3.1 and 3.2, this feature requires a trace flag. For more info, see [Unmigrate remote data (Stretch Database)](../../Topics/TopicNameNotContainA/Unmigrate-remote-data--Stretch-Database-.md).  
  
-   You can now use a federated service account for SQL Server to communicate with the remote Azure SQL Database server when certain conditions are true. In CTP 3.1 and 3.2, this option is not available in the Enable Database for Stretch wizard. You have to use the ALTER DATABASE statement to configure Stretch Database with this option. In CTP 3.1 and 3.2, this feature also requires a trace flag. For more info, see [Enable Stretch Database for a database](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md) and [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc).  
  
-   Stretch Database is now compatible with Always On.  
  
    -   You can enable Stretch on a database that already belongs to an Always On availability group.  
  
    -   You can also add a database that's already enabled for Stretch to an Always On availability group.  
  
 **[CTP 3.3]** Stretch Database now includes the following features and enhancements.  
  
-   You can now add, alter, and drop columns on Stretch-enabled tables.  
  
-   You can create, alter, and drop indexes on Stretch-enabled tables.  
  
-   When you use the Enable Database for Stretch Wizard to create the remote Azure SQL Database, the wizard creates a database with a default 10 TB of storage, with the option to expand the database up to 60 TB.  
  
-   You can now enable Transparent Data Encryption (TDE) on the remote Azure SQL Database if TDE is  enabled on the SQL Server database. For more info, see [Transparent Data Encryption (TDE)](https://msdn.microsoft.com/library/bb934049.aspx) and  [Transparent Data Encryption with Azure SQL Database](https://msdn.microsoft.com/library/dn948096.aspx)  
  
-   The remote Azure SQL Database used by Stretch Database now supports geo-restore. Geo-restore provides the ability to restore a database from a geo-redundant backup to create a new database in any supported Azure region. Geo-restore works in the same way for Stretch Database and for Azure SQL Database. For more info, see [Azure SQL Database Geo-Restore](https://azure.microsoft.com/en-us/blog/azure-sql-database-geo-restore/).  
  
-   Stretch Database now provides full support for point in time restore. After you restore your SQL Server database to a point in time and reauthorize the connection to the remote Azure SQL Database, Stretch Database reconciles the remote data to the same point in time. For more info about point in time restore in SQL Server, see [Restore a SQL Server Database to a Point in Time (Full Recovery Model)](../../Topics/TopicNameContainA/Restore-a-SQL-Server-Database-to-a-Point-in-Time--Full-Recovery-Model-.md). For info about the stored procedure that you have to run after a restore to reauthorize the connection to the remote SQL Database, see [sys.sp_rda_reauthorize_db (Transact-SQL)](assetId:///f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd).  
  
-   The option to use a federated service account for SQL Server to communicate with the remote Azure SQL Database server when certain conditions are true is now available in the Enable Database for Stretch wizard. In CTP 3.3 this feature still requires a trace flag. For more info, see [Get started by running the Enable Database for Stretch Wizard](../../Topics/TopicNameNotContainA/Get-started-by-running-the-Enable-Database-for-Stretch-Wizard.md).  
  
-   The option to specify a predicate no longer requires a trace flag. For more info, see [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md), [Select rows to migrate by using a filter predicate (Stretch Database)](../../Topics/TopicNameContainA/Select-rows-to-migrate-by-using-a-filter-predicate--Stretch-Database-.md), and [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1).  
  
-   In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], when you disable Stretch Database at the table level, you can now choose whether to copy the remote data back to SQL Server or to abandon the remote data. For more info, see [Disable Stretch Database and bring back remote data](../../Topics/TopicNameNotContainA/Disable-Stretch-Database-and-bring-back-remote-data.md).  
  
-   The option to unmigrate the data that Stretch Database has migrated to Azure no longer requires a trace flag. For more info, see [Unmigrate remote data (Stretch Database)](../../Topics/TopicNameNotContainA/Unmigrate-remote-data--Stretch-Database-.md).  
  
-   The **Enable Database for Stretch** Wizard includes many improvements. Here are some highlights.  
  
    -   On the **Select database tables** page, the wizard identifies tables that have blocking issues. You can search for a table and sort the list of tables by various columns. You can select temporal history tables.  
  
    -   On the **Configure Azure deployment** page, the wizard supports both SQL Server and Azure Active Directory authentication.  You can optionally use a federated service account for SQL Server to communicate with the remote Azure SQL Database server when certain conditions are met.  
  
    -   On the **Enable network settings** page, the wizard detects the IP and subnet range of the SQL Server.  
  
    -   On the **Results** page, the wizard provides info about Azure costs and pricing.  
  
 **[RC0]** Stretch Database now includes the following features and enhancements.  
  
-   A preview of a new version of Stretch Database on Azure that supports 60 TB of data is now available. To register for preview access, go to [SQL Server Stretch Database preview](https://azure.microsoft.com/en-us/services/sql-server-stretch-database/request/).  
  
-   The option to use a federated service account for SQL Server to communicate with the remote Azure SQL Database server when certain conditions are true no longer requires a trace flag. For more info, see [Enable Stretch Database for a database](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md).  
  
 **[RC1]** Stretch Database now includes the following features and enhancements.  
  
-   With the release of SQL Server 2016 Release Candidate 1 (RC1), the SQL Server Stretch Database service on Microsoft Azure is now the default data storage service on Azure for Stretch Database. The service lets you scale SQL Server with up to 1 petabyte of cloud storage to make warm and cold data available to users at low cost. You no longer have to sign up to preview the new service. For more info about the new service, see [SQL Server Stretch Database](https://azure.microsoft.com/services/sql-server-stretch-database/). For info about pricing for the new service, see [SQL Server Stretch Database Pricing](https://azure.microsoft.com/en-us/pricing/details/sql-server-stretch-database/).  
  
     When you use the Enable Database for Stretch Wizard in RC1 to create a new Azure server, the server now uses the Stretch Database service on Azure in place of Azure SQL Database.  
  
     If you have databases and tables on which you enabled Stretch Database before RC1, you have remote data stored in Azure SQL Database. After you install RC1, you can no longer access remote data stored in SQL Database. If you want to keep the remote data, you have to bring it back to SQL Server before you install RC1. After you install RC1, you can re-enable Stretch Database on those databases and tables, and the new Azure server will use the new Stretch Database service on Azure in place of Azure SQL Database. For info about how to bring back your remote data, see [Disable Stretch Database and bring back remote data](../../Topics/TopicNameNotContainA/Disable-Stretch-Database-and-bring-back-remote-data.md).  
  
-   You can now create a table that's enabled for Stretch Database by running the CREATE TABLE statement. For more info, see [CREATE TABLE (Transact-SQL)](assetId:///1e068443-b9ea-486a-804f-ce7b6e048e8b)and [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md).  
  
 **[RC3]** Stretch Database now includes the following features and enhancements.  
  
-   In the Enable Database for Stretch Wizard, you can now specify a simple date-based predicate to select rows to migrate. For more info, see [Get started by running the Enable Database for Stretch Wizard](../../Topics/TopicNameNotContainA/Get-started-by-running-the-Enable-Database-for-Stretch-Wizard.md).  
  
###  <a name="ForeignKey"></a> Foreign Key Relationship Limits  
 **[CTP 3.3]** A table can reference a maximum of 253 other tables and columns as foreign keys (outgoing references). [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] increases the limit for the number of other table and columns that can reference columns in a single table (incoming references), from 253 to 10,000. For restrictions, see [Create Foreign Key Relationships](../../Topics/TopicNameNotContainA/Create-Foreign-Key-Relationships.md).  
  
###  <a name="UTF8"></a> Support for UTF-8  
 **[RC0]** [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2), and [OPENROWSET](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17) now support the UTF-8 code page. For more information, see those topics and [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md).  
  
###  <a name="DefaultDB"></a> New Default Database Size and Autogrow Values  
 **[RC0]** New values for the model database and default values for new databases (which are based on model). The initial size of the data and log files is now 8 MB. The default auto-growth of data and log files is now 64MB.  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="TSQL"></a> Transact-SQL Enhancements  
 **[CTP 2.0]** Numerous enhancements support the features described in the other sections of this topic. The following additional enhancements are available.  
  
 The TRUNCATE TABLE statement now permits the truncation of specified partitions. For more information, see [TRUNCATE TABLE (Transact-SQL)](assetId:///3d544eed-3993-4055-983d-ea334f8c5c58).  
  
 [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1) now allows many alter column actions to be performed while the table remains available.  
  
 The full-text index DMV [sys.dm_fts_index_keywords_position_by_document (Transact-SQL)](assetId:///0d70184f-baa2-411b-a32d-a4c5af890edd) returns the location of keywords in documents. This DMV has also been added in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] SP2 and [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)] SP1.  
  
 A new query hint **NO_PERFORMANCE_SPOOL** can prevent a spool operator from being added to query plans. This can improve performance when many concurrent queries are running with spool operations. For more information, see [Query Hints (Transact-SQL)](assetId:///66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d).  
  
 The [FORMATMESSAGE (Transact-SQL)](assetId:///83f18102-2035-4a87-acd0-8d96d03efad5) statement is enhances to accept a msg_string argument.  
  
 The maximum index key size for NONCLUSTERED indexes has been increased to 1700 bytes.  
  
 **[CTP 3.0]** New DROP IF syntax is added for drop statements related to AGGREGATE, ASSEMBLY, COLUMN, CONSTRAINT, DATABASE, DEFAULT, FUNCTION, INDEX, PROCEDURE, ROLE, RULE, SCHEMA, SECURITY POLICY, SEQUENCE, SYNONYM, TABLE, TRIGGER, TYPE, USER, and VIEW. See individual syntax topics for syntax.  
  
 **[CTP 3.0]** A MAXDOP option has been added to [DBCC CHECKTABLE (Transact-SQL)](assetId:///0d6cb620-eb58-4745-8587-4133a1b16994), [DBCC CHECKDB (Transact-SQL)](assetId:///2c506167-0b69-49f7-9282-241e411910df), and [DBCC CHECKFILEGROUP (Transact-SQL)](assetId:///8c70bf34-7570-4eb6-877a-e35064a1380a) to specify the degree of parallelism.  
  
 **[CTP 3.0]** SESSION_CONTEXT can now be set. Includes the [SESSION_CONTEXT (Transact-SQL)](assetId:///b6bdbc54-331a-43cc-ab3d-3872d6a12100) function, [CURRENT_TRANSACTION_ID (Transact-SQL)](assetId:///82cd9f92-d935-45a0-a433-620d6e15b467) function, and the [sp_set_session_context (Transact-SQL)](assetId:///7a3a3b2a-1408-4767-a376-c690e3c1fc5b) procedure.  
  
 **[CTP 3.0]**  
 **Advanced Analytics Extensions** allow users to execute scripts written in a supported language such as R. [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] supports R by introducing the [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df) stored procedure, and the [external scripts enabled Server Configuration Option](../../Topics/TopicNameNotContainA/external-scripts-enabled-Server-Configuration-Option.md). For more information, see [SQL Server R Services](../../Topics/TopicNameNotContainA/SQL-Server-R-Services.md).  
  
 **[RC1]** Additional support for R: The ability to create an external resource pool. For more information, see [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](assetId:///8cc798ad-c395-461c-b7ff-8c561c098808).  New catalog views and DMVs ([sys.resource_governor_external_resource_pools (Transact-SQL)](assetId:///75063e36-a91b-496f-9936-88f3d57bd447) and [sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)](assetId:///e32fac49-5161-47c0-8540-af3fe730c00c)). Additional arguments are available for [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df) and [CREATE WORKLOAD GROUP (Transact-SQL)](assetId:///d949e540-9517-4bca-8117-ad8358848baa). Additional columns are added to some of the existing resource governor catalog views and DMVs.  
  
 **[CTP 3.0]** The [CREATE USER](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80) syntax is enhanced with the ALLOW_ENCRYPTED_VALUE_MODIFICATIONS option to support the Always Encrypted feature. For more information see [Migrate Sensitive Data Protected by Always Encrypted](../../Topics/TopicNameNotContainA/Migrate-Sensitive-Data-Protected-by-Always-Encrypted.md).  
  
 **[CTP 3.1]** The [COMPRESS (Transact-SQL)](assetId:///c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88) and [DECOMPRESS (Transact-SQL)](assetId:///738d56be-3870-4774-b112-3dce27becc11) functions convert values into and out of the GZIP algorithm.  
  
 **[CTP 3.1]** The  [DATEDIFF_BIG (Transact-SQL)](assetId:///19ac1693-3cfa-400d-bf83-20a9cb46599a) and [AT TIME ZONE (Transact-SQL)](assetId:///311f682f-7f1b-43b6-9ea0-24e36b64f73a) functions and the [sys.time_zone_info (Transact-SQL)](assetId:///3f51a9a4-75f8-4a11-9552-8bf6118b68da) view are added to support date and time interactions.  
  
 **[CTP 3.1]** A credential can now be created at the database level (in addition to the server level credential that was previously available). For more information, see [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).  
  
 **[CTP 3.3]** Eight new properties are added to [SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a): InstanceDefaultDataPath, InstanceDefaultLogPath, ProductBuild, ProductBuildType, ProductMajorVersion, ProductMinorVersion, ProductUpdateLevel, and ProductUpdateReference.  
  
 **[CTP 3.3]** The input length limit of 8,000 bytes for the [HASHBYTES (Transact-SQL)](assetId:///0ea6a4d1-313e-4f70-b939-dd2cd570f6d6) function is removed.  
  
 **[RC0]** New string functions [STRING_SPLIT (Transact-SQL)](assetId:///3273dbf3-0b4f-41e1-b97e-b4f67ad370b9) and [STRING_ESCAPE (Transact-SQL)](assetId:///2163bc7a-3816-4304-9c40-8954804f5465) are added.  
  
 **[RC0]** Autogrow options: Trace flag 1117 is replaced by the AUTOGROW_SINGLE_FILE and AUTOGROW_ALL_FILES option of ALTER DATABASE, and trace flag 1117 has no affect. For more information, see [ALTER DATABASE File and Filegroup Options (Transact-SQL)](assetId:///1f635762-f7aa-4241-9b7a-b51b22292b07) and the new is_autogrow_all_files column of [sys.filegroups (Transact-SQL)](assetId:///9e851f72-1f8e-4515-a25d-152ebc12ed56).  
  
 **[RC0]** Allocation of mixed extents: For user databases, default allocation for the first 8 pages of an object will change from using mixed page extents to using uniform extents. Trace flag 1118 is replaced with the SET MIXED_PAGE_ALLOCATION option of ALTER DATABASE, and trace flag 1118 has no affect. For more information, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc), and the new `is_mixed_page_allocation_on` column of [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="SystemTable"></a> System View Enhancements  
 **[CTP 2.0]** Two new views support row level security. For more information, see [sys.security_predicates (Transact-SQL)](assetId:///c7a2f28c-98da-463d-8b8a-8e5619e2c6a6) and [sys.security_policies (Transact-SQL)](assetId:///35362f5b-e601-4049-9e1d-c5307e823831).  
  
 Seven new views support the Query Store feature. For more information, see [Query Store Catalog Views](assetId:///43d5466a-89e2-4e59-b87e-a2a78e59a1de).  
  
 24 new columns are added to [sys.dm_exec_query_stats (Transact-SQL)](assetId:///eb7b58b8-3508-4114-97c2-d877bcb12964) provide information about memory grants.  
  
 Two new query hints (MIN_GRANT_PERCENT and MAX_GRANT_PERCENT) are added to specify memory grants. See [Query Hints (Transact-SQL)](assetId:///66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d).  
  
 **[CTP 2.2]** [sys.dm_exec_session_wait_stats (Transact-SQL)](assetId:///df84842a-71eb-4fda-b448-5953cf9985dc) provides a per session report similar to the server wide [sys.dm_os_wait_stats (Transact-SQL)](assetId:///568d89ed-2c96-4795-8a0c-2f3e375081da).  
  
 **[CTP 2.3]** [sys.dm_exec_function_stats (Transact-SQL)](assetId:///4c3d6a02-08e4-414b-90be-36b89a0e5a3a) provides execution statistics regarding scalar valued functions.  
  
 **[RC0]** Beginning with [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], entries in [sys.dm_db_index_usage_stats (Transact-SQL)](assetId:///d06a001f-0f72-4679-bc2f-66fff7958b86) are retained as they were prior to [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)].  
  
 **[RC0]** Information about statements submitted to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can be returned by the new dynamic management function [sys.dm_exec_input_buffer (Transact-SQL)](assetId:///fb34a560-bde9-4ad9-aa96-0d4baa4fc104).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="Security"></a> Security Enhancements  
  
###  <a name="RLS"></a> Row-Level Security  
 **[CTP 2.0]** Row-level security introduces predicate based access control. It features a flexible, centralized, predicate-based evaluation that can take into consideration metadata (such as labels) or any other criteria the administrator determines as appropriate. The predicate is used as a criterion to determine whether or not the user has the appropriate access to the data based on user attributes. Label based access control can be implemented by using predicate based access control. For more information, see [Row-Level Security](../../Topics/TopicNameNotContainA/Row-Level-Security.md).  
  
 **[CTP 2.3]** Row-level security is supported for memory-optimized tables.  
  
 **[CTP 3.0]** Row-level security adds support for block predicates.  SESSION_CONTEXT can now be set for use in a security policy.  
  
###  <a name="TCE"></a> Always Encrypted  
 **[CTP 2.0]** With Always Encrypted, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer’s trusted environment and not on the server. Always Encrypted secures customer data so DBAs do not have access to plain text data. Encryption and decryption of data happens transparently at the driver level minimizing changes that have to be made to existing applications. For more information, see [Always Encrypted (Database Engine)](../../Topics/TopicNameNotContainA/Always-Encrypted--Database-Engine-.md).  
  
 **[CTP 3.0]** [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] enhancements related to dialog boxes, and the [Always Encrypted Wizard](../../Topics/TopicNameNotContainA/Always-Encrypted-Wizard.md).  
  
 **[CTP 3.0]** Elimination of some restrictions.  
  
 **[CTP 3.0]** The word **DEFINITION** was removed from column master keys. The `CREATE COLUMN MASTER KEY DEFINITION` statement becomes `CREATE COLUMN MASTER KEY`. **sys.column_master_key_definitions** is renamed to **sys.column_master_keys**. The **column_master_key_definition_id** column in **sys.column_encryption_key_values** is now **column_master_key_id**.  
  
 **[CTP 3.0]** The COLUMN MASTER KEY argument of [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](assetId:///517fe745-d79b-4aae-99a7-72be45ea6acb) has been renamed to COLUMN_MASTER_KEY.  
  
 **[CTP 3.0]** Built-in support for using column master keys stored in hardware security modules (HSMs) that provide Crypto API (CAPI) or Cryptography API - Next Generation (CNG).  
  
 **[CTP 3.0]** The [CREATE USER](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80) syntax is enhanced with the ALLOW_ENCRYPTED_VALUE_MODIFICATIONS option to support the Always Encrypted feature. For more information see [Migrate Sensitive Data Protected by Always Encrypted](../../Topics/TopicNameNotContainA/Migrate-Sensitive-Data-Protected-by-Always-Encrypted.md).  
  
###  <a name="Masking"></a> Dynamic Data Masking  
 **[CTP 2.0]** Dynamic data masking limits sensitive data exposure by masking it to non-privileged users. Dynamic data masking helps prevent unauthorized access to sensitive data by enabling customers to designate how much of the sensitive data to reveal with minimal impact on the application layer. It’s a policy-based security feature that hides the sensitive data in the result set of a query over designated database fields, while the data in the database is not changed. For more information, see [Dynamic Data Masking](../../Topics/TopicNameNotContainA/Dynamic-Data-Masking.md).  
  
 **[CTP 3.0]** Adds a random data mask for numeric data. Adds support for all data types, memory optimized tables, SELECT INTO and INSERT INTO operations, import/export support, cursors, and syntax highlighting support in [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)]. Adds a data mask called random.  
  
###  <a name="Perms"></a> New Permissions  
 **[CTP 2.0]** The **ALTER ANY SECURITY POLICY** permission is available as part of the implementation of row level security.  
  
 The **ALTER ANY MASK** and **UNMASK** permissions are available as part of the implementation of dynamic data masking.  
  
 The **ALTER ANY COLUMN ENCRYPTION KEY**, **VIEW ANY COLUMN ENCRYPTION KEY**, **ALTER ANY COLUMN MASTER KEY DEFINITION**, and **VIEW ANY COLUMN MASTER KEY DEFINITION** permissions are available as part of the implementation of the Always Encrypted feature.  
  
 The **ALTER ANY EXTERNAL DATA SOURCE** and **ALTER ANY EXTERNAL FILE FORMAT** permissions are visible in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] but only apply to the [!INCLUDE[ssAPS](../../Topics/TopicNameNotContainA/tokens/ssAPS_md.md)] ([!INCLUDE[ssDW](../../Topics/TopicNameNotContainA/tokens/ssDW_md.md)]).  
  
 **[CTP 3.0]** The **EXECUTE ANY EXTERNAL SCRIPT** permissions are available as part of the support for R scripts.  
  
 **[CTP 3.0]** The **ALTER ANY DATABASE SCOPED CONFIGURATION** permissions is available to authorize the use of the [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a) statement.  
  
###  <a name="TDE"></a> Transparent Data Encryption  
 **[CTP 2.0]** Transparent Data Encryption has been enhanced with support for Intel AES-NI hardware acceleration of encryption. This will reduce the CPU overhead of turning on Transparent Data Encryption.  
  
 [Top](#Top)  
  
###  <a name="AES"></a> AES Encryption for Endpoints  
 **[CTP 2.3]** The default encryption for endpoints is changed from RC4 to AES.  
  
###  <a name="newcredentialtype"></a> New Credential Type  
 **[CTP 3.1]** A credential can now be created at the database level (in addition to the server level credential that was previously available). For more information, see [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](assetId:///fe830577-11ca-44e5-953b-2d589d54d045).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="HighAvailability"></a> High Availability Enhancements  
 **[CTP 3.2]** SQL Server 2016 CTP Standard Edition now supports Always On Basic Availability Groups. Basic availability groups provide support for a primary and secondary replica. This capability replaces the obsolete Database Mirroring technology for high availability. For more information about the differences between basic and advanced availability groups, see [Basic Availability Groups (Always On Availability Groups)](../../Topics/TopicNameNotContainA/Basic-Availability-Groups--Always-On-Availability-Groups-.md).  
  
 **[CTP 2.0]** Load-balancing of read-intent connection requests is now supported across a set of read-only replicas. The previous behavior always directed connections to the first available read-only replica in the routing list. For more information, see [Configure load-balancing across read-only replicas](../../Topics/TopicNameNotContainA/Configure-Read-Only-Routing-for-an-Availability-Group--SQL-Server-.md#loadbalancing).  
  
 The number of replicas that support automatic failover has been increased from two to three.  
  
 Group Managed Service Accounts are now supported for Always On Failover Clusters. For more information, see [Group Managed Service Accounts](https://technet.microsoft.com/library/hh831782.aspx). For Windows Server 2012 R2, an update is required to avoid temporary downtime after a password change. To obtain the update, see [gMSA-based services can't log on after a password change in a Windows Server 2012 R2 domain](https://support.microsoft.com/kb/2998082/).  
  
 [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] supports distributed transactions and the DTC on Windows Server 2016. For more information, see [SQL Server 2016 Support for DTC and Always On Availablity Groups](../../Topics/TopicNameNotContainA/Cross-Database-Transactions-and-Distributed-Transactions-for-Always-On-Availability-Groups-and-Database-Mirroring--SQL-Server-.md#dtcsupport).  
  
 You can now configure [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] to failover when a database goes offline. This change requires the setting the **DB_FAILOVER** option to **ON** in the [CREATE AVAILABILITY GROUP (Transact-SQL)](assetId:///a3d55df7-b4e4-43f3-a14b-056cba36ab98) or [ALTER AVAILABILITY GROUP (Transact-SQL)](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a) statements.  
  
 **[CTP 2.2]** Always On now supports encrypted databases. The Availability Group wizards now prompt you for a password for any databases that contain a database master key when you create a new Availability Group or when you add databases or add replicas to an existing Availability Group.  
  
 **[RC0]** Two availability groups in two separate Windows Server Failover Clusters (WSFC) can now be combined into a Distributed Availability Group. For more information, see [Distributed Availability Groups (Always On Availability Groups)](../../Topics/TopicNameNotContainA/Distributed-Availability-Groups--Always-On-Availability-Groups-.md).  
  
 **[RC0]** Direct seeding allows a secondary replica to be automatically seeded over the network (rather than manual seeding that requires a physical backup of the target database to be restored on the secondary). Direct seeding is specified by setting **SEEDING_MODE=AUTOMATIC** in the [CREATE AVAILABILITY GROUP (Transact-SQL)](assetId:///a3d55df7-b4e4-43f3-a14b-056cba36ab98) or [ALTER AVAILABILITY GROUP (Transact-SQL)](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a) statements. You must also specify **GRANT CREATE ANY DATABASE** with [ALTER AVAILABILITY GROUP (Transact-SQL)](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a) on each secondary replica that is used with direct seeding.  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="Repl"></a> Replication Enhancements  
 **[CTP 3.0]** Replication of memory-optimized tables are now supported. For more information, see [Replication to Memory-Optimized Table Subscribers](../../Topics/TopicNameNotContainA/Replication-to-Memory-Optimized-Table-Subscribers.md).  
  
 **[CTP 3.0]** Replication is now supported to [!INCLUDE[ssSDSfull](../../Topics/TopicNameContainA/tokens/ssSDSfull_md.md)]. For more information, see [Replication to SQL Database](../../Topics/TopicNameNotContainA/Replication-to-SQL-Database.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
##  <a name="Tools"></a> Tools Enhancements  
  
###  <a name="SSMS"></a> Management Studio  
 **[SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/hh213248.aspx)**  
  
 **[CTP 2.0]** [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] supports the Active Directory Authentication Library (ADAL) which is under development for connecting to Microsoft Azure. This replaces the certificate-based authentication used in [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)][!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)].  
  
 [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] installation requires installing .NET 4.6 as a pre-requisite. .NET 4.6 will be automatically installed by setup when [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] is installed.  
  
 **[CTP 3.0]** A new query result grid option supports keeping Carriage Return/Line Feed (newline characters) when copying or saving text from the results grid. Set this from the Tools/Options menu.  
  
 **[RC0]** SQL Server Management Tools is no longer installed from the main feature tree; for details see [Install SQL Server Management Tools with SSMS](../../Topics/TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md).  
  
 [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] installation requires installing .NET 4.6.1 as a pre-requisite. .NET 4.6.1 will be automatically installed by setup when [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] is installed.  
  
###  <a name="UA"></a> Upgrade Advisor  
 **[CTP 2.2]** SQL Server 2016 Upgrade Advisor Preview 1 is a standalone tool that enables users of prior versions to run a set of upgrade rules against their SQL Server database to pinpoint breaking and behavior changes and deprecated features as well as providing help with the adoption of new features such as Stretch Database.  
  
 You can download Upgrade Advisor Preview 1  [here](https://www.microsoft.com/en-us/download/details.aspx?id=48119) or you can install it by using the Web Platform Installer.  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Top](#Top)  
  
## See Also  
 [What's New in SQL Server 2016](../../Topics/TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md)   
 [SQL Server 2016 Release Notes](../../Topics/TopicNameNotContainA/SQL-Server-2016-Release-Notes.md)   
 [Install SQL Server Management Tools with SSMS](../../Topics/TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md)