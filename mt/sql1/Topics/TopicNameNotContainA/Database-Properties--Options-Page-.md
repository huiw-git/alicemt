---
title: "Database Properties (Options Page)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-04-29
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3447987-5507-4630-ac35-58821b72354d
caps.latest.revision: 68
caps.handback.revision: 0
manager: jhubbard
---
# Database Properties (Options Page)
Use this page to view or modify options for the selected database. For more information about the options available on this page, see [ALTER DATABASE SET Options (Transact-SQL)](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) and [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a).  
  
## Page Header  
 **Collation**  
 Specify the collation of the database by selecting from the list. For more information, see [Set or Change the Database Collation](../../Topics/TopicNameNotContainA/Set-or-Change-the-Database-Collation.md).  
  
 **Recovery model**  
 Specify one of the following models for recovering the database: **Full**, **Bulk-Logged**, or **Simple**. For more information about recovery models, see [Recovery Models (SQL Server)](../../Topics/TopicNameNotContainA/Recovery-Models--SQL-Server-.md).  
  
 **Compatibility level**  
 Specify the latest version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that the database supports. Possible values are  **SQL Server 2014 (120)**,  **SQL Server 2012 (110)**, and **SQL Server 2008 (100)**. When a SQL Server 2005 database is upgraded to SQL Server 2014, the compatibility level for that database is changed from 90 to 100.  The 90 compatibility level is not supported in SQL Server 2014. For more information, see [ALTER DATABASE Compatibility Level (Transact-SQL)](assetId:///ca5fd220-d5ea-4182-8950-55d4101a86f6).  
  
 **Containment type**  
 Specify none or partial to designate if this is a contained database. For more information about contained databases, see [Contained Databases](../../Topics/TopicNameNotContainA/Contained-Databases.md). The server property **Enable Contained Databases** must be set to **TRUE** before a database can be configured as contained.  
  
> [!IMPORTANT]  
>  Enabling partially contained databases delegates control over access to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to the owners of the database. For more information, see [Security Best Practices with Contained Databases](../../Topics/TopicNameNotContainA/Security-Best-Practices-with-Contained-Databases.md).  
  
## Automatic  
 **Auto Close**  
 Specify whether the database shuts down cleanly and frees resources after the last user exits. Possible values are **True** and **False**. When **True**, the database is shut down cleanly and its resources are freed after the last user logs off.  
  
 Auto Create Incremental Statistics  
 Specify whether to use the incremental option when per partition statistics are created. For information about incremental statistics, see [CREATE STATISTICS (Transact-SQL)](assetId:///b23e2f6b-076c-4e6d-9281-764bdb616ad2).  
  
 **Auto Create Statistics**  
 Specify whether the database automatically creates missing optimization statistics. Possible values are **True** and **False**. When **True**, any missing statistics needed by a query for optimization are automatically built during optimization. For more information, see [CREATE STATISTICS](assetId:///b23e2f6b-076c-4e6d-9281-764bdb616ad2).  
  
 **Auto Shrink**  
 Specify whether the database files are available for periodic shrinking. Possible values are **True** and **False**. For more information, see [Shrink a Database](../../Topics/TopicNameContainA/Shrink-a-Database.md).  
  
 **Auto Update Statistics**  
 Specify whether the database automatically updates out-of-date optimization statistics. Possible values are **True** and **False**. When **True**, any out-of-date statistics needed by a query for optimization are automatically built during optimization. For more information, see [CREATE STATISTICS](assetId:///b23e2f6b-076c-4e6d-9281-764bdb616ad2).  
  
 **Auto Update Statistics Asynchronously**  
 When **True**, queries that initiate an automatic update of out-of-date statistics will not wait for the statistics to be updated before compiling. Subsequent queries will use the updated statistics when they are available.  
  
 When **False**, queries that initiate an automatic update of out-of-date statistics, wait until the updated statistics can be used in the query optimization plan.  
  
 Setting this option to **True** has no effect unless **Auto Update Statistics** is also set to **True**.  
  
## Containment  
 In a contained databases, some settings usually configured at the server level can be configured at the database level.  
  
 **Default Fulltext Language LCID**  
 Specifies a default language for full-text indexed columns. Linguistic analysis of full-text indexed data is dependent on the language of the data. The default value of this option is the language of the server. For the language that corresponds to the displayed setting, see [sys.fulltext_languages (Transact-SQL)](assetId:///2ed6b53d-1cf2-4763-9d58-36ea24a610ef).  
  
 **Default Language**  
 The default language for all new contained database users, unless otherwise specified.  
  
 **Nested Triggers Enabled**  
 Allows triggers to fire other triggers. Triggers can be nested to a maximum of 32 levels. For more information, see the "Nested Triggers" section in [CREATE TRIGGER (Transact-SQL)](assetId:///edeced03-decd-44c3-8c74-2c02f801d3e7).  
  
 **Transform Noise Words**  
 Suppress an error message if noise words, that is stopwords, cause a Boolean operation on a full-text query to return zero rows. For more information, see [transform noise words Server Configuration Option](../../Topics/TopicNameNotContainA/transform-noise-words-Server-Configuration-Option.md).  
  
 **Two Digit Year Cutoff**  
 Indicates the highest year number that can be entered as a two-digit year. The year listed and the previous 99 years can be entered as a two-digit year. All other years must be entered as a four-digit year.  
  
 For example, the default setting of 2049 indicates that a date entered as '3/14/49' will be interpreted as March 14, 2049, and a date entered as '3/14/50' will be interpreted as March 14, 1950. For more information, see [Configure the two digit year cutoff Server Configuration Option](../../Topics/TopicNameNotContainA/Configure-the-two-digit-year-cutoff-Server-Configuration-Option.md).  
  
## Cursor  
 **Close Cursor on Commit Enabled**  
 Specify whether cursors close after the transaction opening the cursor has committed. Possible values are **True** and **False**. When **True**, any cursors that are open when a transaction is committed or rolled back are closed. When **False**, such cursors remain open when a transaction is committed. When **False**, rolling back a transaction closes any cursors except those defined as INSENSITIVE or STATIC. For more information, see [SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)](assetId:///7b976154-98ce-4a06-bbae-7e59c34211f7).  
  
 **Default Cursor**  
 Specify default cursor behavior. When **True**, cursor declarations default to LOCAL. When **False**, [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] cursors default to GLOBAL.  
  
## Database Scoped Configurations  
 In SQL Server 2016 and in Azure SQL Database, there are a number of configuration properties that can be scoped to the database level. For more information for all of these settings, see [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](assetId:///63373c2f-9a0b-431b-b9d2-6fa35641571a).  
  
 **Legacy Cardinality Estimation**  
 Specify the query optimizer cardinality estimation model for the primary independent of the compatibility level of the database. This is equivalent to [Trace Flag 9481](https://support.microsoft.com/en-us/kb/2801413).  
  
 **Legacy Cardinality Estimation for Secondary**  
 Specify the query optimizer cardinality estimation model for secondaries, if any, independent of the compatibility level of the database. This is equivalent to [Trace Flag 9481](https://support.microsoft.com/en-us/kb/2801413).  
  
 **Max DOP**  
 Specify the default [MAXDOP](https://msdn.microsoft.com/en-us/library/ms189094.aspx) setting for the primary that should be used for statements.  
  
 **Max DOP for Secondary**  
 Specify the default [MAXDOP](https://msdn.microsoft.com/en-us/library/ms189094.aspx) setting for secondaries, if any, that should be used for statements.  
  
 **Parameter Sniffing**  
 Enables or disables parameter sniffing on the primary. This is equivalent to [Trace Flag 4136](https://support.microsoft.com/en-us/kb/980653).  
  
 **Parameter Sniffing for Secondary**  
 Enables or disables parameter sniffing on secondaries, if any. This is equivalent to [Trace Flag 4136](https://support.microsoft.com/en-us/kb/980653).  
  
 **Query Optimizer Fixes**  
 Enables or disables query optimization hotfixes on the primary regardless of the compatibility level of the database. This is equivalent to [Trace Flag 4199](https://support.microsoft.com/en-us/kb/974006).  
  
 **Query Optimizer Fixes for Secondary**  
 Enables or disables query optimization hotfixes on secondaries, if any, regardless of the compatibility level of the database. This is equivalent to [Trace Flag 4199](https://support.microsoft.com/en-us/kb/974006).  
  
## FILESTREAM  
 **FILESTREAM Directory Name**  
 Specify the directory name for the FILESTREAM data associated with the selected database.  
  
 **FILESTREAM Non-transacted Access**  
 Specify one of the following options for non-transactional access through the file system to FILESTREAM data stored in FileTables: **OFF**, **READ_ONLY**, or **FULL**. If FILESTREAM is not enabled on the server, this value is set to OFF and is disabled. For more information, see [FileTables (SQL Server)](../../Topics/TopicNameNotContainA/FileTables--SQL-Server-.md).  
  
## Miscellaneous  
 **ANSI NULL Default**  
 Allow null values for all user-defined data types or columns that are not explicitly defined as **NOT NULL** during a **CREATE TABLE** or **ALTER TABLE** statement (the default state). For more information, see [SET ANSI_NULL_DFLT_ON (Transact-SQL)](assetId:///8c925924-a466-4c8b-aeb2-7e0d341f32db) and [SET ANSI_NULL_DFLT_OFF (Transact-SQL)](assetId:///8ed5c512-f5de-4741-a18a-de85a3041295).  
  
 **ANSI NULLS Enabled**  
 Specify the behavior of the Equals (`=`) and Not Equal To (`<>`) comparison operators when used with null values. Possible values are **True** (on) and **False** (off). When **True**, all comparisons to a null value evaluate to UNKNOWN. When **False**, comparisons of non-UNICODE values to a null value evaluate to **True** if both values are NULL. For more information, see [SET ANSI_NULLS](assetId:///aae263ef-a3c7-4dae-80c2-cc901e48c755).  
  
 **ANSI Padding Enabled**  
 Specify whether ANSI padding is on or off. Permissible values are **True** (on) and **False** (off). For more information, see [SET ANSI_PADDING](assetId:///92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0).  
  
 **ANSI Warnings Enabled**  
 Specify ISO standard behavior for several error conditions. When **True**, a warning message is generated if null values appear in aggregate functions (such as SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP, or COUNT). When **False**, no warning is issued. For more information, see [SET ANSI_WARNINGS (Transact-SQL)](assetId:///f82aaab0-334f-427b-89b0-de4af596b4fa).  
  
 **Arithmetic Abort Enabled**  
 Specify whether the database option for arithmetic abort is enabled or not. Possible values are **True** and **False**. When **True**, an overflow or divide-by-zero error causes the query or batch to terminate. If the error occurs in a transaction, the transaction is rolled back. When **False**, a warning message is displayed, but the query, batch, or transaction continues as if no error occurred. For more information, see [SET ARITHABORT (Transact-SQL)](assetId:///f938a666-fdd1-4233-b97f-719f27b1a0e6).  
  
 **Concatenate Null Yields Null**  
 Specify the behavior when null values are concatenated. When the property value is **True**, **string** + NULL returns NULL. When **False**, the result is **string**. For more information, see [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](assetId:///3091b71c-6518-4eb4-88ab-acae49102bc5).  
  
 **Cross-database Ownership Chaining Enabled**  
 This read-only value indicates if cross-database ownership chaining has been enabled. When **True**, the database can be the source or target of a cross-database ownership chain. Use the ALTER DATABASE statement to set this property.  
  
 **Date Correlation Optimization Enabled**  
 When **True**, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] maintains correlation statistics between any two tables in the database that are linked by a FOREIGN KEY constraint and have **datetime** columns.  
  
 When **False**, correlation statistics are not maintained.  
  
 **Numeric Round-Abort**  
 Specify how the database handles rounding errors. Possible values are **True** and **False**. When **True**, an error is generated when loss of precision occurs in an expression. When **False**, losses of precision do not generate error messages, and the result is rounded to the precision of the column or variable storing the result. For more information, see [SET NUMERIC_ROUNDABORT (Transact-SQL)](assetId:///d20e74f1-b8da-466c-b180-9d8a8b851a77).  
  
 **Parameterization**  
 When **SIMPLE**, queries are parameterized based on the default behavior of the database. When **FORCED**, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] parameterizes all queries in the database.  
  
 **Quoted Identifiers Enabled**  
 Specify whether [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] keywords can be used as identifiers (an object or variable name) if enclosed in quotation marks. Possible values are **True** and **False**. For more information, see [SET QUOTED_IDENTIFIER (Transact-SQL)](assetId:///10f66b71-9241-4a3a-9292-455ae7252565).  
  
 **Recursive Triggers Enabled**  
 Specify whether triggers can be fired by other triggers. Possible values are **True** and **False**. When set to **True**, this enables recursive firing of triggers. When set to **False**, only direct recursion is prevented. To disable indirect recursion, set the nested triggers server option to 0 using sp_configure. For more information, see [Create Nested Triggers](../../Topics/TopicNameNotContainA/Create-Nested-Triggers.md).  
  
 **Trustworthy**  
 When displaying **True**, this read-only option indicates that [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] allows access to resources outside the database under an impersonation context established within the database. Impersonation contexts can be established within the database using the EXECUTE AS user statement or the EXECUTE AS clause on database modules.  
  
 To have access, the owner of the database also needs to have the AUTHENTICATE SERVER permission at the server level.  
  
 This property also allows the creation and execution of unsafe and external access assemblies within the database. In addition to setting this property to **True**, the owner of the database must have the EXTERNAL ACCESS ASSEMBLY or UNSAFE ASSEMBLY permission at the server level.  
  
 By default, all user databases and all system databases (with the exception of **MSDB**) have this property set to **False**. The value cannot be changed for the **model** and **tempdb** databases.  
  
 TRUSTWORTHY is set to **False** whenever a database is attached to the server.  
  
 The recommended approach for accessing resources outside the database under an impersonation context is to use certificates and signatures as apposed to the **Trustworthy** option.  
  
 To set this property, use the ALTER DATABASE statement.  
  
 **VarDecimal Storage Format Enabled**  
 This option is read-only starting with [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)]. When **True**, this database is enabled for the vardecimal storage format. Vardecimal storage format cannot be disabled while any tables in the database are using it. In [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later versions, all databases are enabled for the vardecimal storage format. This option uses [sp_db_vardecimal_storage_format](assetId:///9920b2f7-b802-4003-913c-978c17ae4542).  
  
## Recovery  
 **Page Verify**  
 Specify the option used to discover and report incomplete I/O transactions caused by disk I/O errors. Possible values are **None**, **TornPageDetection**, and **Checksum**. For more information, see [Manage the suspect_pages Table (SQL Server)](../../Topics/TopicNameNotContainA/Manage-the-suspect_pages-Table--SQL-Server-.md).  
  
 **Target Recovery Time (Seconds)**  
 Specifies the maximum bound on the time, expressed in seconds, to recover the specified database in the event of a crash. For more information, see [Database Checkpoints (SQL Server)](../../Topics/TopicNameNotContainA/Database-Checkpoints--SQL-Server-.md).  
  
## State  
 **Database Read Only**  
 Specify whether the database is read only. Possible values are **True** and **False**. When **True**, users can only read data in the database. Users cannot modify the data or database objects; however, the database itself can be deleted using the DROP DATABASE statement. The database cannot be in use when a new value for the **Database Read Only** option is specified. The master database is the exception, and only the system administrator can use master while the option is being set.  
  
 **Database State**  
 View the current state of the database. It is not editable. For more information about **Database State**, see [Database States](../../Topics/TopicNameNotContainA/Database-States.md).  
  
 **Restrict Access**  
 Specify which users may access the database. Possible values are:  
  
-   **Multiple**  
  
     The normal state for a production database, allows multiple users to access the database at once.  
  
-   **Single**  
  
     Used for maintenance actions, only one user is allowed to access the database at once.  
  
-   **Restricted**  
  
     Only members of the db_owner, dbcreator, or sysadmin roles can use the database.  
  
 **Encryption Enabled**  
 When **True**, this database is enabled for database encryption. A Database Encryption Key is required for encryption. For more information, see [Transparent Data Encryption (TDE)](../../Topics/TopicNameNotContainA/Transparent-Data-Encryption--TDE-.md).  
  
## See Also  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)