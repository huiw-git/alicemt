---
title: Faster temp table and table variable by using memory optimization
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38512a22-7e63-436f-9c13-dde7cf5c2202
---
# Faster temp table and table variable by using memory optimization
  
If you use temporary tables, or use table variables, consider conversions of them to leverage In-Memory features for much faster performance. The code changes are small.  
  
Before implementing in production, you must first verify that your hardware has sufficient amounts of active memory.  
  
This article describes:  
  
- Scenarios which argue in favor of conversion to In-Memory.  
- Technical steps for implementing the conversions to In-Memory.  
- Prerequisites before conversion to In-Memory.  
  
  
#### Three long code T-SQL samples  
  
In this article there are three Transact-SQL code samples that look long. But most of their bulk is preliminaries like pre-dropping then creating a table or type. The real interest is in certain small portions of the code, which are mentioned for emphasis.  
  
Each sample can be run as is. Each sample highlights the usefulness of memory-optimized table variables:  
  
- Section F: Speed comparison to demonstrate that a table variable performs much faster if it is memory-optimized.  
  - The two halves of this sample are very similar to each other.  
- Section G: Demonstrates how to overcome the limitations that In-Memory features have regarding:  
  - The FROM clause on the T-SQL UPDATE statement.  
  - CURSOR.  
- Section H: Demonstrates how to simulate the T-SQL MERGE statement in an In-Memory context.  
  - Most of the code in section H is very similar to the code in section G.  
  
  
Each runnable code sample requires that the prerequisite FILEGROUP in section E to already be created.  
  
  
  
## A. Basics of memory-optimized table variables  
  
A memory-optimized table variable provides great efficiency by using the same memory-optimized algorithm and data structures that are used by memory-optimized tables. The efficiency is maximized when the table variable is accessed from within a natively compiled module.  
  
  
A memory-optimized table variable:  
  
- Is stored only in memory, and has no component on disk.  
- Involves no IO activity.  
- Involves no tempdb utilization or contention.  
- Lifetime is scoped to the current user session only.  
- Can be passed into a stored proc as a table-valued parameter (TVP).  
- Must have at least one index, either hash or nonclustered.  
  - For a hash index, the bucket count should be 1.5 times the number of expected unique index keys. For details see [Indexes for Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Indexes-for-Memory-Optimized-Tables.md).  
  
  
#### Nonclustered index consumes more active memory  
  
A nonclustered index uses more active memory when the index is on a memory-optimized table *variable* than it does when on a memory-optimized *table*. The larger the index key, the more the difference increases.  
  
If the memory-optimized table variable is accessed only with one exact key value per access, a hash index might be a better choice than a nonclustered index. However, if you cannot estimate the appropriate BUCKET_COUNT, a NONCLUSTERED index is a good second choice.  
  
  
#### Object types  
  
In-Memory OLTP provides the following objects:  
  
- Natively compiled modules, including:  
  - stored procedures  
  - functions  
  - triggers  
- Memory-optimized tables  
  - Durability = SCHEMA_AND_DATA  
  - Durability = SCHEMA_ONLY  
- Memory-optimized table variables  
  - Must be declared in two steps (rather than inline):  
    - `CREATE TYPE my_type AS TABLE ...;` , then  
    - `DECLARE @mytablevariable my_type;`.  
  
  
#### DLL  
  
SQL Server generates a DLL file for each memory-optimized table type.  
  
- The compilation to create the DLL occurs when the type is created, and does not wait for a variable of the type to be declared.  
- The DLL includes functions for accessing and retrieving data from the table variable.  
  
  
  
## B. Scenario: Replace global tempdb &#x23;&#x23;table  
  
Suppose you have the following global temporary table.  
  
  
  
  
	CREATE TABLE ##tempGlobalB  
	(  
		Column1   INT   NOT NULL ,  
		Column2   NVARCHAR(4000)  
	);  
  
  
  
  
Consider replacing the global temporary table with the following memory-optimized table that has DURABILITY = SCHEMA_ONLY.  
  
  
  
  
	CREATE TABLE dbo.soGlobalB  
	(  
		Column1   INT   NOT NULL   INDEX ix1 NONCLUSTERED,  
		Column2   NVARCHAR(4000)  
	)  
		WITH  
			(MEMORY_OPTIMIZED = ON,  
			DURABILITY        = SCHEMA_ONLY);  
  
  
  
  
#### B.1 Steps  
  
The conversion from global temporary to SCHEMA_ONLY is the following steps:  
  
  
1. Create the **dbo.soGlobalB** table, one time, just as you would any traditional on-disk table.  
2. From your Transact-SQL, remove the create of the **&#x23;&#x23;tempGlobalB** table.  
3. In your T-SQL, replace all mentions of **&#x23;&#x23;tempGlobalB** with **dbo.soGlobalB**.  
  
  
## C. Scenario: Replace session tempdb &#x23;table  
  
The preparations for replacing a session temporary table involve more T-SQL than for the earlier global temporary table scenario. Happily the extra T-SQL does not mean any more effort is needed to accomplish the conversion.  
  
Suppose you have the following session temporary table.  
  
  
  
  
	CREATE TABLE #tempSessionC  
	(  
		Column1   INT   NOT NULL ,  
		Column2   NVARCHAR(4000)  
	);  
  
  
  
  
First, create the following table-value function to filter on **@@spid**. The function will be usable by all SCHEMA_ONLY tables that you convert from session temporary tables.  
  
  
  
  
	CREATE FUNCTION dbo.fn_SpidFilter(@SpidFilter smallint)  
		RETURNS TABLE  
		WITH SCHEMABINDING , NATIVE_COMPILATION  
	AS  
		RETURN  
			SELECT 1 AS fn_SpidFilter  
				WHERE @SpidFilter = @@spid;  
  
  
  
  
Second, create the SCHEMA_ONLY table, plus a security policy on the table.  
  
  
Note that each memory-optimized table must have at least one index.  
  
- For table dbo.soSessionC a HASH index might be better, if we calculate the appropriate BUCKET_COUNT. But for this sample we simplify to a NONCLUSTERED index.  
  
  
  
  
	CREATE TABLE dbo.soSessionC  
	(  
		Column1     INT         NOT NULL,  
		Column2     NVARCHAR(4000)  NULL,  
  
		SpidFilter  SMALLINT    NOT NULL   DEFAULT (@@spid),  
  
		INDEX ix_SpidFiler NONCLUSTERED (SpidFilter),  
		--INDEX ix_SpidFilter HASH  
		--    (SpidFilter) WITH (BUCKET_COUNT = 64),  
		  
		CONSTRAINT CHK_soSessionC_SpidFilter  
			CHECK ( SpidFilter = @@spid ),  
	)  
		WITH  
			(MEMORY_OPTIMIZED = ON,  
			 DURABILITY = SCHEMA_ONLY);  
	go  
  
  
	CREATE SECURITY POLICY dbo.soSessionC_SpidFilter_Policy  
		ADD FILTER PREDICATE dbo.fn_SpidFilter(SpidFilter)  
		ON dbo.soSessionC  
		WITH (STATE = ON);  
	go  
  
  
  
  
Third, in your general T-SQL code:  
  
1. Erase any CREATE TABLE statements for the old session temporary table.  
2. Replace the old table name with the new name:  
  - _Old:_ &#x23;tempSessionC  
  - _New:_ dbo.soSessionC  
  
  
  
## D. Scenario: Table variable can be MEMORY_OPTIMIZED=ON  
  
  
A traditional table variable represents a table in the tempdb database. For much faster performance you can memory-optimize your table variable.  
  
Here is the T-SQL for a traditional table variable. Its scope ends when either the batch or the session ends.  
  
  
  
  
	DECLARE @tvTableD TABLE  
		( Column1   INT   NOT NULL ,  
		  Column2   CHAR(10) );  
  
  
  
  
#### D.1 Convert inline to explicit  
  
The preceding syntax is said to create the table variable *inline*. The inline syntax does not support memory-optimization. So let us convert the inline syntax to the explicit syntax for the TYPE.  
  
*Scope:* The TYPE definition created by the first go-delimited batch persists even after the server is shutdown and restarted. But after the first go delimiter, the declared table @tvTableC persists only until the next go is reached and the batch ends.  
  
  
  
  
	CREATE TYPE dbo.typeTableD  
		AS TABLE  
		(  
			Column1  INT   NOT NULL ,  
			Column2  CHAR(10)  
		);  
	go  
		  
	SET NoCount ON;  
	DECLARE @tvTableD dbo.typeTableD  
	;  
	INSERT INTO @tvTableD (Column1) values (1), (2)  
	;  
	SELECT * from @tvTableD;  
	go  
  
  
  
  
#### D.2 Convert explicit on-disk to memory-optimized  
  
A memory-optimized table variable does not reside in tempdb. Memory-optimization results in speed increases that are often 10 times faster or more.  
  
The conversion to memory-optimized is achieved in only one step. Enhance the explicit TYPE creation to be the following, which adds:  
  
- An index. Again, each memory-optimized table must have at least one index.  
- MEMORY_OPTIMIZED = ON.  
  
  
  
  
	CREATE TYPE dbo.typeTableD  
		AS TABLE  
		(  
			Column1  INT   NOT NULL   INDEX ix1,  
			Column2  CHAR(10)  
		)  
		WITH  
			(MEMORY_OPTIMIZED = ON);  
  
  
  
  
Done.  
  
  
## E. Prerequisite FILEGROUP for SQL Server  
  
On Microsoft SQL Server, to use memory-optimized features, your database must have a FILEGROUP that is declared with **MEMORY_OPTIMIZED_DATA**.  
  
- Azure SQL Database does not use any FILEGROUP.  
  
  
*Prerequisite:* The following Transact-SQL code for a FILEGROUP is a prerequisite for the long T-SQL code samples in later sections of this article.  
  
1. You must use SSMS.exe or another tool that can submit T-SQL.  
2. Paste the sample FILEGROUP T-SQL code into SSMS.  
3. Edit the T-SQL to change its specific names and directory paths to your liking.  
  - All directories in the FILENAME value must preexist, except the final directory must not preexist.  
4. Run your edited T-SQL.  
  - There is no need to run the FILEGROUP T-SQL more than one time, even if you repeatedly adjust and rerun the speed comparison T-SQL in the next subsection.  
  
  
  
  
	ALTER DATABASE InMemTest2  
		REMOVE FILE FileMemOptim3a;  -- Removes the FgMemOptim3a\ directory.  
	go  
	ALTER DATABASE InMemTest2  
		REMOVE FILEGROUP FgMemOptim3;  
	go  
  
  
	ALTER DATABASE InMemTest2  
		ADD FILEGROUP FgMemOptim3  
			CONTAINS MEMORY_OPTIMIZED_DATA;  
	go  
	ALTER DATABASE InMemTest2  
		ADD FILE  
		(  
			NAME = N'FileMemOptim3a',  
			FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016RC3\MSSQL\DATA\FileMemOptim3a\'  
					 --  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016RC3\MSSQL\DATA\    preexisted.  
		)  
		TO FILEGROUP FgMemOptim3;  
	go  
  
  
  
  
For more information about `ALTER DATABASE ... ADD/REMOVE` for FILE and FILEGROUP, see:  
  
- [ALTER DATABASE File and Filegroup Options (Transact-SQL)](ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20(Transact-SQL).xml)  
- [The Memory Optimized Filegroup](../../Topics\TopicNameNotContainA/The-Memory-Optimized-Filegroup.md)  
- [Resource Governor Resource Pool](../../Topics\TopicNameNotContainA/Resource-Governor-Resource-Pool.md)  
  - If you test on a computer that has little active memory, you might occasionally see a error Msg 701 about the resource pool. If a second test attempt still suffers Msg 701, click the documentation link.  
  
  
  
## F. Quick test to prove speed improvement  
  
  
This section provides Transact-SQL code that you can run to test and compare the speed gain for INSERT-DELETE from using a memory-optimized table variable. The code is composed of two halves that are nearly the same, except in the first half the table type is memory-optimized.  
  
The comparison test lasts about 7 seconds. To run the sample:  
  
1. *Prerequisite:* You must already have run the FILEGROUP T-SQL from the previous section.  
2. Run the following T-SQL INSERT-DELETE script.  
  - Notice the 'GO 5001' statement, which resubmits the T-SQL 5001 times. You can adjust the number and rerun.  
  
  
  
  
	PRINT ' ';  
	PRINT '---- Next, memory-optimized, faster. ----';  
  
	DROP TYPE IF EXISTS dbo.typeTableC_mem;  
	go  
	CREATE TYPE dbo.typeTableC_mem  -- !!  Memory-optimized.  
		 AS TABLE  
		 (  
			  Column1  INT NOT NULL INDEX ix1,  
			  Column2  CHAR(10)  
		 )  
		 WITH  
			  (MEMORY_OPTIMIZED = ON);  
	go  
	DECLARE @dateString_Begin nvarchar(64) =  
		Convert(nvarchar(64), GetUtcDate(), 121);  
	PRINT Concat(@dateString_Begin, '  = Begin time, _mem.');  
	go  
	SET NoCount ON;  
	DECLARE @tvTableC dbo.typeTableC_mem;  -- !!  
  
	INSERT INTO @tvTableC (Column1) values (1), (2);  
	INSERT INTO @tvTableC (Column1) values (3), (4);  
	DELETE @tvTableC;  
  
	GO 5001  
  
	DECLARE @dateString_End nvarchar(64) =  
		Convert(nvarchar(64), GetUtcDate(), 121);  
	PRINT Concat(@dateString_End, '  = End time, _mem.');  
	go  
	DROP TYPE IF EXISTS dbo.typeTableC_mem;  
	go  
  
	---- End memory-optimized.  
	-------------------------------------------------  
	---- Start traditional on-disk.  
  
	PRINT ' ';  
	PRINT '---- Next, tempdb based, slower. ----';  
  
	DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
	go  
	CREATE TYPE dbo.typeTableC_tempdb  -- !!  Traditional tempdb.  
		AS TABLE  
		(  
			Column1  INT NOT NULL ,  
			Column2  CHAR(10)  
		);  
	go  
	DECLARE @dateString_Begin nvarchar(64) =  
		Convert(nvarchar(64), GetUtcDate(), 121);  
	PRINT Concat(@dateString_Begin, '  = Begin time, _tempdb.');  
	go  
	SET NoCount ON;  
	DECLARE @tvTableC dbo.typeTableC_tempdb;  -- !!  
  
	INSERT INTO @tvTableC (Column1) values (1), (2);  
	INSERT INTO @tvTableC (Column1) values (3), (4);  
	DELETE @tvTableC;  
  
	GO 5001  
  
	DECLARE @dateString_End nvarchar(64) =  
		Convert(nvarchar(64), GetUtcDate(), 121);  
	PRINT Concat(@dateString_End, '  = End time, _tempdb.');  
	go  
	DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
	go  
	----  
  
	PRINT '---- Tests done. ----';  
  
	go  
  
	/*** Actual output, SQL Server 2016:  
  
	---- Next, memory-optimized, faster. ----  
	2016-04-20 00:26:58.033  = Begin time, _mem.  
	Beginning execution loop  
	Batch execution completed 5001 times.  
	2016-04-20 00:26:58.733  = End time, _mem.  
  
	---- Next, tempdb based, slower. ----  
	2016-04-20 00:26:58.750  = Begin time, _tempdb.  
	Beginning execution loop  
	Batch execution completed 5001 times.  
	2016-04-20 00:27:05.440  = End time, _tempdb.  
	---- Tests done. ----  
	***/  
  
  
  
  
Finally, when you are done, you might want to run the `ALTER DATABASE ... REMOVE` statements for the FILE and FILEGROUP, as a clean-up.  
  
  
  
## G. Code for scenario of UPDATE FROM and CURSOR  
  
This section describes a specific scenario in which a memory-optimized table type is an excellent option.  
  
On a memory-optimized table, any trigger must also be memory-optimized. A natively compiled module is limited to a large subset of Transact-SQL. Among the limitations are the following:   
  
- No CURSOR.  
- On an UPDATE statement:  
  - No FROM clause.  
  - No subquery such as in the WHERE clause.  
  
Here is the T-SQL UPDATE statement we would use if the trigger and its host table were both traditional on-disk objects. But we cannot use this UPDATE in an In-Memory context:  
  
  
  
  
	UPDATE dbo.Table1  
		SET LastUpdated = SysDateTime()  
		FROM  
				 dbo.Table1 t  
			JOIN Inserted   i ON t.Id = i.Id;  
  
  
  
  
The sample T-SQL code in this section demonstrates a workaround that provides good performance. The workaround is implemented in a memory-optimized trigger. Crucial to notice in the code are:  
  
- The type named dbo.Type1, which is a memory-optimized table type.  
- The WHILE loop in the trigger.  
  - The loop retrieves the rows from Inserted one at a time.  
  
  
  
  
	DROP TRIGGER IF EXISTS dbo.tr_a_u_Table1;  
	go  
	DROP TYPE    IF EXISTS dbo.Type1;  
	go  
	DROP TABLE   IF EXISTS dbo.Table1;  
	go  
	-----------------------------  
  
	CREATE TABLE dbo.Table1  
	(  
		Id           INT        NOT NULL  PRIMARY KEY NONCLUSTERED,  
		Column2      INT        NOT NULL,  
		LastUpdated  DATETIME2  NOT NULL  DEFAULT (SysDateTime())  
	)  
		WITH (MEMORY_OPTIMIZED = ON);  
	go  
  
  
	CREATE TYPE dbo.Type1 AS TABLE  
	(  
		Id       INT NOT  NULL,  
  
		RowID    INT NOT  NULL  IDENTITY,  
		INDEX ix_RowID (RowID DESC)  
	)   
		WITH (MEMORY_OPTIMIZED = ON);  
	go  
	-----------------------------  
	-----------------------------  
  
	CREATE TRIGGER dbo.tr_a_u_Table1  
		ON dbo.Table1  
		WITH NATIVE_COMPILATION, SCHEMABINDING  
		AFTER UPDATE  
	AS BEGIN ATOMIC WITH  
		(  
		TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
		LANGUAGE = N'us_english'  
		)  
	DECLARE @tabvar1 dbo.Type1;  
  
	INSERT @tabvar1 (Id)   
		SELECT Id FROM Inserted;  
  
	DECLARE  
		@i INT = 1,  @Id INT,  
		@max INT = SCOPE_IDENTITY();  
  
	---- Loop as a workaround to simulate a cursor for  
	----   an In-Memory context.  
	---- Iterate over the rows in the memory-optimized table  
	----   variable, in our natively compiled trigger module.  
  
	WHILE @i <= @max  
	BEGIN  
		SELECT @Id = Id  
			FROM @tabvar1  
			WHERE RowID = @i;  
  
		UPDATE dbo.Table1  
			SET LastUpdated = SysDateTime()  
			WHERE Id = @Id;  
  
		SET @i += 1;  
	END  
	END  
	go  
	-----------------------------  
	-----------------------------  
  
	SET NoCount ON;  
  
	INSERT dbo.Table1 (Id, Column2)  
		VALUES (1,9), (2,9), (3,600);  
  
	WAITFOR DELAY '00:00:01';  
  
	SELECT N'BEFORE-Update' AS [BEFORE-Update], *  
		FROM dbo.Table1  
		ORDER BY Id;  
  
	UPDATE dbo.Table1  
		SET   Column2 += 1  
		WHERE Column2 <= 99;  
  
	SELECT N'AFTER--Update' AS [AFTER--Update], *  
		FROM dbo.Table1  
		ORDER BY Id;  
	go  
	-----------------------------  
  
	DROP TRIGGER IF EXISTS dbo.tr_a_u_Table1;  
	go  
	DROP TYPE    IF EXISTS dbo.Type1;  
	go  
	DROP TABLE   IF EXISTS dbo.Table1;  
	go  
  
	/**** Actual output:  
  
	BEFORE-Update   Id   Column2   LastUpdated  
	BEFORE-Update   1       9      2016-04-20 21:18:42.8394659  
	BEFORE-Update   2       9      2016-04-20 21:18:42.8394659  
	BEFORE-Update   3     600      2016-04-20 21:18:42.8394659  
  
	AFTER--Update   Id   Column2   LastUpdated  
	AFTER--Update   1      10      2016-04-20 21:18:43.8529692  
	AFTER--Update   2      10      2016-04-20 21:18:43.8529692  
	AFTER--Update   3     600      2016-04-20 21:18:42.8394659  
	****/  
  
  
  
  
  
## H. Code for scenario of MERGE  
  
  
The Transact-SQL code sample in this section demonstrates how you can simulate the T-SQL MERGE statement in a natively compiled stored procedure. Most of the preliminary code is very similar to the previous code sample about UPDATE FROM. The biggest differences are inside the WHILE loop.  
  
Here is the T-SQL MERGE statement that you wish was supported inside a native proc, and that the code sample simulates.  
  
  
  
  
	MERGE INTO dbo.Table1 t  
		USING @tvp v  
		ON t.Column1 = v.c1  
		WHEN MATCHED THEN   
			UPDATE SET Column2 = v.c2  
		WHEN NOT MATCHED THEN  
			INSERT (Column1, Column2) VALUES (v.c1, v.c2);  
  
  
  
  
Here is the T-SQL to achieve the workaround and simulate MERGE.  
  
  
  
  
	DROP PROCEDURE IF EXISTS dbo.usp_merge1;  
	go  
	DROP TYPE IF EXISTS dbo.Type1;  
	go  
	DROP TABLE IF EXISTS dbo.Table1;  
	go  
	-----------------------------  
  
	CREATE TABLE dbo.Table1  
	(  
		Column1  INT  NOT NULL  PRIMARY KEY NONCLUSTERED,  
		Column2  INT  NOT NULL  
	)   
		WITH (MEMORY_OPTIMIZED = ON);  
	go  
  
	CREATE TYPE dbo.Type1 AS TABLE  
	(  
		c1  INT  NOT NULL,  
		c2  INT  NOT NULL,  
  
		RowID    INT  NOT NULL  IDENTITY(1,1),  
		INDEX ix_RowID (RowID DESC)  
	)   
		WITH (MEMORY_OPTIMIZED = ON);  
	go  
	-----------------------------  
	-----------------------------  
  
	CREATE PROCEDURE dbo.usp_merge1   
		@tvp1 dbo.Type1 READONLY  
		WITH  
		NATIVE_COMPILATION, SCHEMABINDING  
	AS   
	BEGIN ATOMIC  
		WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
			  LANGUAGE = N'us_english')  
  
		DECLARE @max INT;  
  
		SELECT @max = MAX(RowID) FROM @tvp1;  
  
		DECLARE  @i INT = 1,  @c1 INT,  @c2 INT;  
  
		WHILE @i <= @max  
		BEGIN  
			SELECT @c1 = c1, @c2 = c2  
				FROM @tvp1  
				WHERE RowID = @i;  
  
			UPDATE dbo.Table1  
				SET   Column2 = @c2  
				WHERE Column1 = @c1;  
  
			IF @@ROWCOUNT=0  
				INSERT INTO dbo.Table1 (Column1, Column2)  
					VALUES (@c1, @c2);  
  
			SET @i += 1;  
		END  
	END  
	go  
	-----------------------------  
	-----------------------------  
  
	INSERT dbo.Table1 VALUES (1,2);  
	go  
  
	SELECT N'Before-MERGE' AS [Before-MERGE], Column1, Column2  
		FROM dbo.Table1;  
	go  
  
	DECLARE @tvp1 dbo.Type1;  
  
	INSERT @tvp1 (c1, c2) VALUES (1,33), (2,4);  
	EXECUTE dbo.usp_merge1 @tvp1;  
	go  
  
	SELECT N'After--MERGE' AS [After--MERGE], Column1, Column2  
		FROM dbo.Table1;  
	go  
	-----------------------------  
  
	DROP PROCEDURE IF EXISTS dbo.usp_merge1;  
	go  
	DROP TYPE IF EXISTS dbo.Type1;  
	go  
	DROP TABLE IF EXISTS dbo.Table1;  
	go  
  
	/****  Actual output:  
  
	Before-MERGE   Column1   Column2  
	Before-MERGE      1         2  
  
	After--MERGE   Column1   Column2  
	After--MERGE      1        33  
	After--MERGE      2         4  
	****/  
  
  
  
  
## I. Predict active memory consumption  
  
You can learn to predict the active memory needs of your memory-optimized tables with the following resources:  
  
- [Memory Optimization Advisor](../../Topics\TopicNameNotContainA/Memory-Optimization-Advisor.md)  
- [Estimate Memory Requirements for Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Estimate-Memory-Requirements-for-Memory-Optimized-Tables.md)  
- [Table and Row Size in Memory-Optimized Tables: Example Calculation](../../Topics\TopicNameNotContainA/Table-and-Row-Size-in-Memory-Optimized-Tables.md)  
  
  
  
## J. See also  
  
  
- [Durability for Memory-Optimized Tables](../../Topics\TopicNameNotContainA/Durability-for-Memory-Optimized-Tables.md)  
- [Defining Durability for Memory-Optimized Objects](../../Topics\TopicNameNotContainA/Defining-Durability-for-Memory-Optimized-Objects.md)  
  
  
  
  
<!--  
CAPS Title: "Faster temp table and table variable by using memory optimization"  
  
https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/  
  
  
[ALTER DATABASE File and Filegroup Options (Transact-SQL)](http://msdn.microsoft.com/library/bb522469.aspx)  
  
[The Memory Optimized Filegroup](http://msdn.microsoft.com/library/dn639109.aspx)  
  
[Resource Governor Resource Pool](http://msdn.microsoft.com/library/hh510189.aspx)  
  
  
[Memory Optimization Advisor](http://msdn.microsoft.com/library/dn284308.aspx)  
  
[Estimate Memory Requirements for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn282389.aspx)  
  
[Table and Row Size in Memory-Optimized Tables: Example Calculation](http://msdn.microsoft.com/library/dn205318.aspx)  
  
  
[Durability for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn553125.aspx)  
  
[Defining Durability for Memory-Optimized Objects](http://msdn.microsoft.com/library/dn553122.aspx)  
  
[Memory-Optimized Table Variables](http://msdn.microsoft.com/library/dn535766.aspx)  
  
  
GeneMi , 2016-05-02  Monday  18:40pm  
-->  
  
  
  
