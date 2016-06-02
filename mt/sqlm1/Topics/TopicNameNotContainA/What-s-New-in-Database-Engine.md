---
title: What&#39;s New in Database Engine
ms.custom: 
  - SQL2016_New_Updated
  - SQL2016_rc1
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
---
# What&#39;s New in Database Engine
This topic summarizes the enhancements introduced in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] release of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)].  The new features and enhancements increase the power and productivity of architects, developers, and administrators who design, develop, and maintain data storage systems.

To review what is new in the other SQL Server components, see [What's New in SQL Server 2016](../../Topics\TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md).

> [!NOTE]
>  [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] is a 64\-bit application. 32\-bit installation is discontinued, though some elements run as 32\-bit components.

#### Try it out

- To download [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], go to  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**![download](../../Images\Image\ImageNotContaina/download.png "download").

- Have an Azure account?  Then go **[Here](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rc0evaluationwindowsserver2012r2/?wt.mc_id=sqL16_vm)** to spin up a Virtual Machine with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] already installed.

![note](../../Images\Image\ImageNotContaina/ssrs_fyi_note.png "ssrs_fyi_note") For the current release notes, see [SQL Server 2016 Release Notes](../../Topics\TopicNameNotContainA/SQL-Server-2016-Release-Notes.md).

##  <a name="Feature"></a> Database Engine Feature Enhancements

###  <a name="columnstore"></a> Columnstore Indexes

This release offers improvements for columnstore indexes including updateable nonclustered columnstore indexes, columnstore indexes on in\-memory tables, and many more new features for operational analytics.

- A read\-only nonclustered columnstore index is updateable after upgrade.  A rebuild of the index is not required to make it updateable.

- There are performance improvements for analytics queries on columnstore indexes,  especially for aggregates and string predicates.

- DMVs and XEvents have supportability improvements.

For more details, see these topics in the [Columnstore Indexes Guide](../../Topics\TopicNameNotContainA/Columnstore-Indexes-Guide.md) section of Books Online:

- [Columnstore Indexes Versioned Feature Summary](../../Topics\TopicNameNotContainA/Columnstore-Indexes-Versioned-Feature-Summary.md) – includes what’s new.

- [Columnstore Indexes Data Loading](../../Topics\TopicNameNotContainA/Columnstore-Indexes-Data-Loading.md)

- [Columnstore Indexes Query Performance](../../Topics\TopicNameNotContainA/Columnstore-Indexes-Query-Performance.md)

- [Get started with Columnstore for real time operational analytics](../../Topics\TopicNameNotContainA/Get-started-with-Columnstore-for-real-time-operational-analytics.md)

- [Columnstore Indexes for Data Warehousing](../../Topics\TopicNameNotContainA/Columnstore-Indexes-for-Data-Warehousing.md)

- [Columnstore Indexes Defragmentation](../../Topics\TopicNameNotContainA/Columnstore-Indexes-Defragmentation.md)


###  <a name="scopedconfiguration"></a> Database Scoped Configurations


The new [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SCOPED%20CONFIGURATION%20\(Transact-SQL\).md) statement gives you control of certain configurations for your particular database. The configuration settings affect application behavior.

The new statement is available in both [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] and [!INCLUDE[sqldbesa](../../Token\Other/sqldbesa_md.md)].



###  <a name="InMemory"></a> In\-Memory OLTP


#### Reduced downtime during upgrade

Upgrade from an earlier build of SQL Server, to SQL Server 2016, no longer runs database recovery. Therefore data size no longer affects the duration of upgrade. For upgrade and attach\/restore from SQL Server 2014, the database is restarted only once.

- [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)

#### @@SPID

The built\-in configuration function @@SPID is now supported in the following:

- Constraints on memory\-optimized tables.
- Natively compiled T\-SQL modules.
  - For a code example, find @@SPID in: [Faster temp table and table variable by using memory optimization](Faster%20temp%20table%20and%20table%20variable%20by%20using%20memory%20optimization\.md).


#### ALTER TABLE is log-optimized, and runs in parallel

Now when you execute an ALTER TABLE statement on a memory-optimized table, only the metadata changes are written to the log. This greatly reduces log IO. Also, most ALTER TABLE scenarios now run in parallel, which can greatly shorten the duration of the statement.

- For non-parallel exceptions, including LOBs, see [Altering Memory-Optimized Tables](Altering%20Memory%2dOptimized%20Tables%2exml).



#### Statistics

[Statistics for memory\-optimized](Statistics%20for%20Memory%2dOptimized%20Tables%2exml) tables are now updated automatically. In addition, sampling is now a supported method to collect statistics, allowing you to avoid the more expensive fullscan method.


#### Parallel scan for memory\-optimized tables

Memory\-optimized tables, and hash indexes, are now scannable in parallel. This improves the performance of analytical queries.

- Traditional disk-based tables and indexes are scannable in parallel.
- Columnstore indexes have always been scannable in parallel.


#### LOBs with large row size for a memory\-optimized table

A memory-optimized table can now have several columns whose combined lengths are longer than the length of the 8060 byte page. An example is a table that has three columns of type `nvarchar(4000)`. In such examples, some columns are now stored off-row. Your queries are blissfully unaware of whether a column is on-row or off-row.

Also, now your table can have [LOB (large object)](Supported%20Data%20Types%20for%20In%2dMemory%20OLTP\.md) type columns, such as `varbinary(max)`.


#### OUTPUT clause in natively compiled stored procedures

In a natively compiled stored procedure, INSERT and UPDATE and DELETE statements can now include the [OUTPUT clause](../Topic/OUTPUT%20Clause%20\(Transact-SQL\).md).


#### Transact\-SQL Improvements for memory-optimized tables

There are several Transact-SQL elements that were not supported for memory-optimized tables in SQL Server 2014, which are now supported in SQL Server 2016:


- UNIQUE indexes are supported.


- FOREIGN KEY references between memory-optimized tables are supported.
  - These foreign keys can reference only a primary key, and cannot reference a unique key.


- CHECK constraints are supported.


- A non-unique index can allow NULL values in its key.


- TRIGGERs are supported on memory-optimized tables.
  - Only triggers that execute after the table operation are supported.
  - Any trigger on a memory-optimized table must use WITH NATIVE_COMPILATION.


- Full support for any code page, any collation, and for Unicode.


- Increased support for [Altering Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Altering-Memory-Optimized-Tables.md):
  - ADD and DROP indexes.
  - Make schema changes.


For overall information, see:

- [Transact-SQL Constructs Not Supported by In-Memory OLTP](Transact\-SQL%20Constructs%20Not%20Supported%20by%20In\-Memory%20OLTP.md)
- [Unsupported SQL Server Features for In-Memory OLTP](Unsupported%20SQL%20Server%20Features%20for%20In-Memory OLTP.md)


#### Transact\-SQL Improvements for natively compiled modules

There are some Transact-SQL elements that were not supported for natively compiled modules in SQL Server 2014, which are now supported in SQL Server 2016:


- Query constructs:
  - UNION and UNION ALL
  - SELECT DISTINCT
  - OUTER JOIN
  - Subqueries in SELECT


- LOBs can now be used in the following ways in a native proc:
  - Declaration of variables.
  - Input parameters received.
  - Parameters passed into string functions, such as into LTrim or Substring, in a native proc.


- Inline (meaning single statement) table-valued functions (TVFs) can now be natively compiled.

- Scalar user-defined functions (UDFs) can now be natively compiled.


- Increased support for a native proc to call:
  - Built\-in [security functions](Security%20Functions%20%28Transact-SQL%29.md).
  - Built-in [math functions](Mathematical%20Functions%20%28Transact-SQL%29.md).


- EXECUTE AS CALLER is no longer required.


For overall information, see:

- [Supported Features for Natively Compiled T-SQL Modules](../../Topics\TopicNameNotContainA/Supported-Features-for-Natively-Compiled-T-SQL-Modules.md)
- [Altering Natively Compiled T-SQL Modules](../../Topics\TopicNameNotContainA/Altering-Natively-Compiled-T-SQL-Modules.md)


#### Performance and scaling improvements

- A database can now have up to [2 terabytes of user data](Estimate%20Memory%20Requirements%20for%20Memory-Optimized Tables.md) in memory\-optimized tables with SCHEMA\_AND\_DATA.

- There are now multiple concurrent threads responsible to [persist to disk the changes to memory-optimized tables](../../Topics\TopicNameNotContainA/Scalability.md).

- Parallel plan support for [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](../../Topics\TopicNameNotContainA/Accessing-Memory-Optimized-Tables-Using-Interpreted-Transact-SQL.md).

#### Enhancements in SQL Server Management Studio

- The [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](../../Topics\TopicNameContainA/Determining-if-a-Table-or-Stored-Procedure-Should-Be-Ported-to-In-Memory-OLTP.md) no longer requires the configuration of data collectors or management data warehouse. The report can now run directly on a production database.

- [PowerShell Cmdlet for Migration Evaluation](../../Topics\TopicNameNotContainA/PowerShell-Cmdlet-for-Migration-Evaluation.md) for evaluating the migration fitness of multiple objects in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.

- Generate migration checklists by right\-clicking on a database, and selecting Tasks > Generate In\-Memory OLTP migration checklists.

#### Cross\-feature support

- Support for using temporal system\-versioning with In\-Memory OLTP. For more information, see [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)

- Query store support for natively compiled code from In\-Memory OLTP workloads. For more information, see [Using the Query Store with In-Memory OLTP](../../Topics\TopicNameNotContainA/Using-the-Query-Store-with-In-Memory-OLTP.md).

- [Row-Level Security in Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Introduction-to-Memory-Optimized-Tables.md)

- [Using Multiple Active Result Sets &#40;MARS&#41;](../Topic/Using%20Multiple%20Active%20Result%20Sets%20\(MARS\).md) connections  can now access memory\-optimized tables and natively compiled stored procedures.

- [Transparent Data Encryption (TDE)](Transparent%20Data%20Encryption%20%28TDE%29%2exml) support. If a database is configured for ENCRYPTION, files in the[The Memory Optimized Filegroup](The%20Memory%20Optimized%20Filegroup%2exml) are now also encrypted.

For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../Topic/In-Memory%20OLTP%20%28In-Memory%20Optimization%29.md).



###  <a name="LiveStats"></a> Live Query Statistics
 [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] provides the ability to view the live execution plan of an active query. This live query plan provides real\-time insights into the query execution process as the controls flow from one query plan operator to another. For more information, see [Live Query Statistics](../../Topics\TopicNameNotContainA/Live-Query-Statistics.md).

###  <a name="QueryStore"></a> Query Store
Query store is a new feature that provides DBAs with insight on query plan choice and performance. It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans. The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review. It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server. The query store presents information by using a [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] dialog box, and lets you force the query to one of the selected query plans. For more information, see [Monitoring Performance By Using the Query Store](../../Topics\TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md).


###  <a name="TT"></a> Temporal Tables
[!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] now supports system-versioned temporal tables. A temporal table is a new type of table that provides correct information about stored facts at any point in time. Each temporal table consists of two tables actually, one for the current data and one for the historical data. The system ensures that when the data changes in the table with the current data the previous values are stored in the historical table. Querying constructs are provided to hide this complexity from users. For more information, see [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md).

###  <a name="StripedBackupToAzure"></a> Striped Backups to Microsoft Azure Blob Storage
In [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], SQL Server backup to URL using the Microsoft Azure Blob storage service now supports striped backups sets using block blobs to support a maximum backup size of 12.8 TB. For examples, see [Code Examples](../../Topics\TopicNameNotContainA/SQL-Server-Backup-to-URL.md).

###  <a name="FileSnapshotBackup"></a> File\-Snapshot Backups to Microsoft Azure Blob Storage
 In [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], SQL Server backup to URL now supports using Azure snapshots to backup databases in which all database files are stored using the Microsoft Azure Blob storage service. For more information, see [File-Snapshot Backups for Database Files in Azure](../../Topics\TopicNameNotContainA/File-Snapshot-Backups-for-Database-Files-in-Azure.md).

###  <a name="ManagedBackup"></a> Managed Backup
 **\[CTP 2.0\]** In [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] SQL Server Managed Backup to Microsoft Azure uses the new block blob storage for backup files. There are also several changes and enhancements to Managed Backup.

-   Support for both automated and custom scheduling of backups.

-   Support backups for system databases.

-   Support for databases that are using the Simple recovery model.

 For more information, see [SQL Server Managed Backup to Microsoft Azure](../../Topics\TopicNameNotContainA/SQL-Server-Managed-Backup-to-Microsoft-Azure.md)

> [!NOTE]
>  For [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], these new managed backup features do not yet have corresponding UI support in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].

###  <a name="TraceFlag"></a> Trace flag 4199 behaviors are enabled
 In general, you do not need to use trace flag 4199 in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] since most of the query optimizer behaviors controlled by this trace flag are enabled unconditionally under the latest compativility level \(130\) in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].


###  <a name="multipleTempDB"></a> TempDB Database
 There are several enhancements to TempDB:

-   Trace Flags 1117 and 1118 are not required for tempdb anymore. If there are multiple tempdb database files all files will grow at the same time depending on growth settings. In addition, all allocations in tempdb will use uniform extents.

-   By default, setup adds as many tempdb files as the CPU count or 8, whichever is lower.

-   During setup, you can configure the number of tempdb database files, initial size, autogrowth and directory placement using the new UI input control on the Database Engine Configuration \- TempDB section of SQL Server Installation Wizard.

-   The default initial size is 8MB and the default autogrowth is 64MB.

-   You can specify multiple volumes for tempdb database files. If multiple directories are specified tempdb data files will be spread across the directories in a round\-robin fashion.

###  <a name="ForJson"></a> Built\-in JSON Support
SQL Server 2016 adds built\-in support for importing and exporting JSON and working with JSON strings. This built-in support includes the following statements and functions.

-   Format query results as JSON, or export JSON, by adding the **FOR JSON** clause to a **SELECT** statement. Use the **FOR JSON** clause, for example, to delegate the formatting of JSON output from your client applications to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more info, see [Format Query Results as JSON with FOR JSON &#40;SQL Server&#41;](../Topic/Format%20Query%20Results%20as%20JSON%20with%20FOR%20JSON%20\(SQL%20Server\).md).

-   Convert JSON data to rows and columns, or import JSON, by calling the **OPENJSON** rowset provider function. Use **OPENJSON** to import JSON data into SQL Server, or convert JSON data to rows and columns for an app or service that can't currently consume JSON directly. For more info, see [Convert JSON Data to Rows and Columns with OPENJSON &#40;SQL Server&#41;](../Topic/Convert%20JSON%20Data%20to%20Rows%20and%20Columns%20with%20OPENJSON%20\(SQL%20Server\).md).

-   The **ISJSON** function tests whether a string contains valid JSON. For more info, see [ISJSON &#40;Transact-SQL&#41;](../Topic/ISJSON%20\(Transact-SQL\).md)

-   The **JSON\_VALUE** function extracts a scalar value from a JSON string.For more info, see [JSON_VALUE &#40;Transact-SQL&#41;](../Topic/JSON_VALUE%20\(Transact-SQL\).md).

-   The **JSON\_QUERY** function extracts an object or an array from a JSON string. For more info, see [JSON_QUERY &#40;Transact-SQL&#41;](../Topic/JSON_QUERY%20\(Transact-SQL\).md).

-   The **JSON\_MODIFY** function updates the value of a property in a JSON string and return the updated JSON string. For more info, see [JSON_MODIFY &#40;Transact-SQL&#41;](../Topic/JSON_MODIFY%20\(Transact-SQL\).md).

###  <a name="bkPolyBase"></a> PolyBase
 PolyBase allows you to use T\-SQL statements to access data stored in Hadoop or Azure Blob Storage and query it in an adhoc fashion. It also lets you query semi\-structured data and join the results with relational data sets stored in SQL Server. PolyBase is optimized for data warehousing workloads and intended for analytical query scenarios.

 For more information, see [PolyBase Guide](../../Topics\TopicNameNotContainA/PolyBase-Guide.md).

###  <a name="stretch"></a> Stretch Database
 Stretch Database is a new feature in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] that migrates your historical data transparently and securely to the Microsoft Azure cloud. You can access your SQL Server data seamlessly regardless of whether it’s on-premises or stretched to the cloud. You set the policy that determines where data is stored, and SQL Server handles the data movement in the background. The entire table is always online and queryable. And, Stretch Database doesn't require any changes to existing queries or applications – the location of the data is completely transparent to the application. For more info, see [Stretch Database](../../Topics\TopicNameNotContainA/Stretch-Database.md).
 
###  <a name="ForeignKey"></a> Foreign Key Relationship Limits
A table can reference a maximum of 253 other tables and columns as foreign keys \(outgoing references\). [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] increases the limit for the number of other table and columns that can reference columns in a single table \(incoming references\), from 253 to 10,000. For restrictions, see [Create Foreign Key Relationships](../../Topics\TopicNameNotContainA/Create-Foreign-Key-Relationships.md).

###  <a name="UTF8"></a> Support for UTF\-8
[bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](../Topic/BULK%20INSERT%20\(Transact-SQL\).md), and [OPENROWSET](../Topic/OPENROWSET%20\(Transact-SQL\).md) now support the UTF\-8 code page. For more information, see those topics and [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md).

###  <a name="DefaultDB"></a> New Default Database Size and Autogrow Values
New values for the model database and default values for new databases \(which are based on model\). The initial size of the data and log files is now 8 MB. The default auto\-growth of data and log files is now 64MB.


##  <a name="TSQL"></a> Transact\-SQL Enhancements
Numerous enhancements support the features described in the other sections of this topic. The following additional enhancements are available.
- The TRUNCATE TABLE statement now permits the truncation of specified partitions. For more information, see [TRUNCATE TABLE &#40;Transact-SQL&#41;](../Topic/TRUNCATE%20TABLE%20\(Transact-SQL\).md).
- [ALTER TABLE &#40;Transact-SQL&#41;](../Topic/ALTER%20TABLE%20\(Transact-SQL\).md) now allows many alter column actions to be performed while the table remains available.
- The full\-text index DMV [sys.dm_fts_index_keywords_position_by_document &#40;Transact-SQL&#41;](../Topic/sys.dm_fts_index_keywords_position_by_document%20\(Transact-SQL\).md) returns the location of keywords in documents. This DMV has also been added in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP2 and [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] SP1.
- A new query hint **NO\_PERFORMANCE\_SPOOL** can prevent a spool operator from being added to query plans. This can improve performance when many concurrent queries are running with spool operations. For more information, see [Query Hints &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).
- The [FORMATMESSAGE &#40;Transact-SQL&#41;](../Topic/FORMATMESSAGE%20\(Transact-SQL\).md) statement is enhances to accept a msg\_string argument.-
 The maximum index key size for NONCLUSTERED indexes has been increased to 1700 bytes.
- New DROP IF syntax is added for drop statements related to AGGREGATE, ASSEMBLY, COLUMN, CONSTRAINT, DATABASE, DEFAULT, FUNCTION, INDEX, PROCEDURE, ROLE, RULE, SCHEMA, SECURITY POLICY, SEQUENCE, SYNONYM, TABLE, TRIGGER, TYPE, USER, and VIEW. See individual syntax topics for syntax.
- A MAXDOP option has been added to [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../Topic/DBCC%20CHECKTABLE%20\(Transact-SQL\).md), [DBCC CHECKDB &#40;Transact-SQL&#41;](../Topic/DBCC%20CHECKDB%20\(Transact-SQL\).md), and [DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](../Topic/DBCC%20CHECKFILEGROUP%20\(Transact-SQL\).md) to specify the degree of parallelism.
- SESSION\_CONTEXT can now be set. Includes the [SESSION_CONTEXT &#40;Transact-SQL&#41;](../Topic/SESSION_CONTEXT%20\(Transact-SQL\).md) function, [CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../Topic/CURRENT_TRANSACTION_ID%20\(Transact-SQL\).md) function, and the [sp_set_session_context &#40;Transact-SQL&#41;](../Topic/sp_set_session_context%20\(Transact-SQL\).md) procedure.
- Advanced Analytics Extensions allow users to execute scripts written in a supported language such as R. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] supports R by introducing the [sp_execute_external_script &#40;Transact-SQL&#41;](../Topic/sp_execute_external_script%20\(Transact-SQL\).md) stored procedure, and the [external scripts enabled Server Configuration Option](../../Topics\TopicNameNotContainA/external-scripts-enabled-Server-Configuration-Option.md). For more information, see [SQL Server R Services](../../Topics\TopicNameNotContainA/SQL-Server-R-Services.md).
- Also to support R, the ability to create an external resource pool. For more information, see [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../Topic/CREATE%20EXTERNAL%20RESOURCE%20POOL%20\(Transact-SQL\).md).  New catalog views and DMVs \([sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../Topic/sys.resource_governor_external_resource_pools%20\(Transact-SQL\).md) and [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../Topic/sys.dm_resource_governor_external_resource_pool_affinity%20\(Transact-SQL\).md)\). Additional arguments are available for [sp_execute_external_script &#40;Transact-SQL&#41;](../Topic/sp_execute_external_script%20\(Transact-SQL\).md) and [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20WORKLOAD%20GROUP%20\(Transact-SQL\).md). Additional columns are added to some of the existing resource governor catalog views and DMVs.
- The [CREATE USER](../Topic/CREATE%20USER%20\(Transact-SQL\).md) syntax is enhanced with the ALLOW\_ENCRYPTED\_VALUE\_MODIFICATIONS option to support the Always Encrypted feature. For more information see [Migrate Sensitive Data Protected by Always Encrypted](../../Topics\TopicNameNotContainA/Migrate-Sensitive-Data-Protected-by-Always-Encrypted.md).
- The [COMPRESS &#40;Transact-SQL&#41;](../Topic/COMPRESS%20\(Transact-SQL\).md) and [DECOMPRESS &#40;Transact-SQL&#41;](../Topic/DECOMPRESS%20\(Transact-SQL\).md) functions convert values into and out of the GZIP algorithm.
- The  [DATEDIFF_BIG &#40;Transact-SQL&#41;](../Topic/DATEDIFF_BIG%20\(Transact-SQL\).md) and [AT TIME ZONE &#40;Transact-SQL&#41;](../Topic/AT%20TIME%20ZONE%20\(Transact-SQL\).md) functions and the [sys.time_zone_info &#40;Transact-SQL&#41;](../Topic/sys.time_zone_info%20\(Transact-SQL\).md) view are added to support date and time interactions.
- A credential can now be created at the database level \(in addition to the server level credential that was previously available\). For more information, see [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20SCOPED%20CREDENTIAL%20\(Transact-SQL\).md).
- Eight new properties are added to [SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md): InstanceDefaultDataPath, InstanceDefaultLogPath, ProductBuild, ProductBuildType, ProductMajorVersion, ProductMinorVersion, ProductUpdateLevel, and ProductUpdateReference.
- The input length limit of 8,000 bytes for the [HASHBYTES &#40;Transact-SQL&#41;](../Topic/HASHBYTES%20\(Transact-SQL\).md) function is removed.
- New string functions [STRING_SPLIT &#40;Transact-SQL&#41;](../Topic/STRING_SPLIT%20\(Transact-SQL\).md) and [STRING_ESCAPE &#40;Transact-SQL&#41;](../Topic/STRING_ESCAPE%20\(Transact-SQL\).md) are added.
- Autogrow options: Trace flag 1117 is replaced by the AUTOGROW\_SINGLE\_FILE and AUTOGROW\_ALL\_FILES option of ALTER DATABASE, and trace flag 1117 has no affect. For more information, see [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md) and the new is\_autogrow\_all\_files column of [sys.filegroups &#40;Transact-SQL&#41;](../Topic/sys.filegroups%20\(Transact-SQL\).md).
- Allocation of mixed extents: For user databases, default allocation for the first 8 pages of an object will change from using mixed page extents to using uniform extents. Trace flag 1118 is replaced with the SET MIXED\_PAGE\_ALLOCATION option of ALTER DATABASE, and trace flag 1118 has no affect. For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md), and the new `is_mixed_page_allocation_on` column of [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md).


##  <a name="SystemTable"></a> System View Enhancements
- Two new views support row level security. For more information, see [sys.security_predicates &#40;Transact-SQL&#41;](../Topic/sys.security_predicates%20\(Transact-SQL\).md) and [sys.security_policies &#40;Transact-SQL&#41;](../Topic/sys.security_policies%20\(Transact-SQL\).md).
- Seven new views support the Query Store feature. For more information, see [Query Store Catalog Views &#40;Transact-SQL&#41;](../Topic/Query%20Store%20Catalog%20Views%20\(Transact-SQL\).md).
- 24 new columns are added to [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_exec_query_stats%20\(Transact-SQL\).md) provide information about memory grants.
- Two new query hints \(MIN\_GRANT\_PERCENT and MAX\_GRANT\_PERCENT\) are added to specify memory grants. See [Query Hints &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).
- [sys.dm_exec_session_wait_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_exec_session_wait_stats%20\(Transact-SQL\).md) provides a per session report similar to the server wide [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_os_wait_stats%20\(Transact-SQL\).md).
- [sys.dm_exec_function_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_exec_function_stats%20\(Transact-SQL\).md) provides execution statistics regarding scalar valued functions.
- Beginning with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], entries in [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../Topic/sys.dm_db_index_usage_stats%20\(Transact-SQL\).md) are retained as they were prior to [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)].
- Information about statements submitted to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can be returned by the new dynamic management function [sys.dm_exec_input_buffer &#40;Transact-SQL&#41;](../Topic/sys.dm_exec_input_buffer%20\(Transact-SQL\).md).


##  <a name="Security"></a> Security Enhancements

###  <a name="RLS"></a> Row\-Level Security
Row\-level security introduces predicate based access control. It features a flexible, centralized, predicate\-based evaluation that can take into consideration metadata \(such as labels\) or any other criteria the administrator determines as appropriate. The predicate is used as a criterion to determine whether or not the user has the appropriate access to the data based on user attributes. Label based access control can be implemented by using predicate based access control. For more information, see [Row-Level Security](../../Topics\TopicNameNotContainA/Row-Level-Security.md).


###  <a name="TCE"></a> Always Encrypted
With Always Encrypted, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer’s trusted environment and not on the server. Always Encrypted secures customer data so DBAs do not have access to plain text data. Encryption and decryption of data happens transparently at the driver level minimizing changes that have to be made to existing applications. For more information, see [Always Encrypted &#40;Database Engine&#41;](../Topic/Always%20Encrypted%20\(Database%20Engine\).md).


###  <a name="Masking"></a> Dynamic Data Masking
Dynamic data masking limits sensitive data exposure by masking it to non\-privileged users. Dynamic data masking helps prevent unauthorized access to sensitive data by enabling customers to designate how much of the sensitive data to reveal with minimal impact on the application layer. It’s a policy\-based security feature that hides the sensitive data in the result set of a query over designated database fields, while the data in the database is not changed. For more information, see [Dynamic Data Masking](../../Topics\TopicNameNotContainA/Dynamic-Data-Masking.md).


###  <a name="Perms"></a> New Permissions
- The **ALTER ANY SECURITY POLICY** permission is available as part of the implementation of row level security.
- The **ALTER ANY MASK** and **UNMASK** permissions are available as part of the implementation of dynamic data masking.
- The **ALTER ANY COLUMN ENCRYPTION KEY**, **VIEW ANY COLUMN ENCRYPTION KEY**, **ALTER ANY COLUMN MASTER KEY DEFINITION**, and **VIEW ANY COLUMN MASTER KEY DEFINITION** permissions are available as part of the implementation of the Always Encrypted feature.
- The **ALTER ANY EXTERNAL DATA SOURCE** and **ALTER ANY EXTERNAL FILE FORMAT** permissions are visible in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] but only apply to the [!INCLUDE[ssAPS](../../Token\Other/ssAPS_md.md)] \([!INCLUDE[ssDW](../../Token\Other/ssDW_md.md)]\).
- The **EXECUTE ANY EXTERNAL SCRIPT** permissions are available as part of the support for R scripts.
 - The **ALTER ANY DATABASE SCOPED CONFIGURATION** permissions is available to authorize the use of the [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SCOPED%20CONFIGURATION%20\(Transact-SQL\).md) statement.

###  <a name="TDE"></a> Transparent Data Encryption
- Transparent Data Encryption has been enhanced with support for Intel AES\-NI hardware acceleration of encryption. This will reduce the CPU overhead of turning on Transparent Data Encryption.

###  <a name="AES"></a> AES Encryption for Endpoints
- The default encryption for endpoints is changed from RC4 to AES.

###  <a name="newcredentialtype"></a> New Credential Type
- A credential can now be created at the database level \(in addition to the server level credential that was previously available\). For more information, see [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20SCOPED%20CREDENTIAL%20\(Transact-SQL\).md).


##  <a name="HighAvailability"></a> High Availability Enhancements
 **\[CTP 3.2\]** SQL Server 2016 CTP Standard Edition now supports Always On Basic Availability Groups. Basic availability groups provide support for a primary and secondary replica. This capability replaces the obsolete Database Mirroring technology for high availability. For more information about the differences between basic and advanced availability groups, see [Basic Availability Groups &#40;Always On Availability Groups&#41;](../Topic/Basic%20Availability%20Groups%20\(Always%20On%20Availability%20Groups\).md).

 **\[CTP 2.0\]** Load\-balancing of read\-intent connection requests is now supported across a set of read\-only replicas. The previous behavior always directed connections to the first available read\-only replica in the routing list. For more information, see [Configure load-balancing across read-only replicas](../Topic/Configure%20Read-Only%20Routing%20for%20an%20Availability%20Group%20\(SQL%20Server\).md#loadbalancing).

 The number of replicas that support automatic failover has been increased from two to three.

 Group Managed Service Accounts are now supported for Always On Failover Clusters. For more information, see [Group Managed Service Accounts](https://technet.microsoft.com/library/hh831782.aspx). For Windows Server 2012 R2, an update is required to avoid temporary downtime after a password change. To obtain the update, see [gMSA\-based services can't log on after a password change in a Windows Server 2012 R2 domain](https://support.microsoft.com/kb/2998082/).

 [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] supports distributed transactions and the DTC on Windows Server 2016. For more information, see [Support for distributed transactions](../Topic/Cross-Database%20Transactions%20and%20Distributed%20Transactions%20for%20Always%20On%20Availability%20Groups%20and%20Database%20Mirroring%20\(SQL%20Server\).md#dtcsupport).

 You can now configure [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] to failover when a database goes offline. This change requires the setting the **DB\_FAILOVER** option to **ON** in the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statements.

 **\[CTP 2.2\]** Always On now supports encrypted databases. The Availability Group wizards now prompt you for a password for any databases that contain a database master key when you create a new Availability Group or when you add databases or add replicas to an existing Availability Group.

 **\[RC0\]** Two availability groups in two separate Windows Server Failover Clusters \(WSFC\) can now be combined into a Distributed Availability Group. For more information, see [Distributed Availability Groups &#40;Always On Availability Groups&#41;](../Topic/Distributed%20Availability%20Groups%20\(Always%20On%20Availability%20Groups\).md).

 **\[RC0\]** Direct seeding allows a secondary replica to be automatically seeded over the network \(rather than manual seeding that requires a physical backup of the target database to be restored on the secondary\). Direct seeding is specified by setting **SEEDING\_MODE\=AUTOMATIC** in the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statements. You must also specify **GRANT CREATE ANY DATABASE** with [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) on each secondary replica that is used with direct seeding.

##  <a name="Repl"></a> Replication Enhancements
- Replication of memory\-optimized tables are now supported. For more information, see [Replication to Memory-Optimized Table Subscribers](../../Topics\TopicNameNotContainA/Replication-to-Memory-Optimized-Table-Subscribers.md).
- Replication is now supported to [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)]. For more information, see [Replication to SQL Database](../../Topics\TopicNameNotContainA/Replication-to-SQL-Database.md).

##  <a name="Tools"></a> Tools Enhancements

###  <a name="SSMS"></a> Management Studio
Download the latest [SQL Server Management Studio \(SSMS\)](https://msdn.microsoft.com/library/mt238290.aspx)

- [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] supports the Active Directory Authentication Library \(ADAL\) which is under development for connecting to Microsoft Azure. This replaces the certificate\-based authentication used in [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)].
- [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] installation requires installing .NET 4.6 as a pre\-requisite. .NET 4.6 will be automatically installed by setup when [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] is installed.
- A new query result grid option supports keeping Carriage Return\/Line Feed \(newline characters\) when copying or saving text from the results grid. Set this from the Tools\/Options menu.
- SQL Server Management Tools is no longer installed from the main feature tree; for details see [Install SQL Server Management Tools with SSMS](../../Topics\TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md).
- [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] installation requires installing .NET 4.6.1 as a pre\-requisite. .NET 4.6.1 will be automatically installed by setup when [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] is installed.

###  <a name="UA"></a> Upgrade Advisor
 **\[CTP 2.2\]** SQL Server 2016 Upgrade Advisor Preview 1 is a standalone tool that enables users of prior versions to run a set of upgrade rules against their SQL Server database to pinpoint breaking and behavior changes and deprecated features as well as providing help with the adoption of new features such as Stretch Database.

 You can download Upgrade Advisor Preview 1  [here](https://www.microsoft.com/en-us/download/details.aspx?id=48119) or you can install it by using the Web Platform Installer.

## See Also
 [What's New in SQL Server 2016](../../Topics\TopicNameNotContainA/What-s-New-in-SQL-Server-2016.md)
 [SQL Server 2016 Release Notes](../../Topics\TopicNameNotContainA/SQL-Server-2016-Release-Notes.md) 
 [Install SQL Server Management Tools with SSMS](../../Topics\TopicNameNotContainA/Install-SQL-Server-Management-Tools-with-SSMS.md)

