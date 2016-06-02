---
title: SQL Server, Deprecated Features Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e95de9d6-c950-41cd-8aaa-be529c6de198
---
# SQL Server, Deprecated Features Object
  The SQLServer:Deprecated Features object in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a counter to monitor the features designated as deprecated. In each case the counter provides a usage count that lists the number of times the deprecated feature was encountered since [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] last started.  
  
 The value of these counters are also available by executing the following statement:  
  
```  
SELECT * FROM sys.dm_os_performance_counters   
WHERE object_name = 'SQLServer:Deprecated Features';  
```  
  
 The following table describes the SQL Server Deprecated Features counter instances.  
  
|SQL Server Deprecated Features counter instances|Description|  
|------------------------------------------------------|-----------------|  
|'\#' and '\#\#' as the name of temporary tables and stored procedures|An identifier was encountered that did not contain any characters other than \#. Use at least one additional character. Occurs once per compilation.|  
|'::' function calling syntax|The :: function calling syntax was encountered for a table\-valued function. Replace with `SELECT column_list FROM` *\< function\_name\>*`()`. For example, replace `SELECT * FROM ::fn_virtualfilestats(2,1)`with `SELECT * FROM sys.fn_virtualfilestats(2,1)`. Occurs once per compilation.|  
|'@' and names that start with '@@' as [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] identifiers|An identifier was encountered that began with @ or @@. Do not use @ or @@ or names that begin with @@ as identifiers. Occurs once per compilation.|  
|ADDING TAPE DEVICE|The deprecated feature sp\_addumpdevice'**tape**' was encountered. Use sp\_addumpdevice'**disk**' instead. Occurs once per use.|  
|ALL Permission|Total number of times the GRANT ALL, DENY ALL, or REVOKE ALL syntax was encountered. Modify the syntax to deny specific permissions. Occurs once per query.|  
|ALTER DATABASE WITH TORN\_PAGE\_DETECTION|Total number of times the deprecated feature TORN\_PAGE\_DETECTION option of ALTER DATABASE has been used since the server instance was started. Use the PAGE\_VERIFY syntax instead. Occurs once per use in a DDL statement.|  
|ALTER LOGIN WITH SET CREDENTIAL|The deprecated feature syntax ALTER LOGIN WITH SET CREDENTIAL or ALTER LOGIN WITH NO CREDENTIAL was encountered. Use ADD or DROP CREDENTIAL syntax instead. Occurs once per compilation.|  
|Azeri\_Cyrilllic\_90|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation.|  
|Azeri\_Latin\_90|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation.|  
|BACKUP DATABASE or LOG TO TAPE|The deprecated feature BACKUP { DATABASE &#124; LOG } TO TAPE or BACKUP { DATABASE &#124; LOG } TO *device\_that\_is\_a\_tape* was encountered.<br /><br /> Use BACKUP { DATABASE &#124; LOG } TO DISK or BACKUP { DATABASE &#124; LOG } TO *device\_that\_is\_a\_disk*, instead. Occurs once per use.|  
|BACKUP DATABASE or LOG WITH MEDIAPASSWORD|The deprecated feature BACKUP DATABASE WITH MEDIAPASSWORD or BACKUP LOG WITH MEDIAPASSWORD was encountered. Do not use WITH MEDIAPASSWORD.|  
|BACKUP DATABASE or LOG WITH PASSWORD|The deprecated feature BACKUP DATABASE WITH PASSWORD or BACKUP LOG WITH PASSWORD was encountered. Do not use WITH PASSWORD.|  
|COMPUTE \[BY\]|The COMPUTE or COMPUTE BY syntax was encountered. Rewrite the query to use GROUP BY with ROLLUP. Occurs once per compilation.|  
|CREATE FULLTEXT CATLOG IN PATH|A CREATE FULLTEXT CATLOG statement with the IN PATH clause was encountered. This clause has no effect in this version of SQL Server. Occurs once per use.|  
|CREATE TRIGGER WITH APPEND|A CREATE TRIGGER statement with the WITH APPEND clause was encountered. Re\-create the whole trigger instead. Occurs once per use in a DDL statement.|  
|CREATE\_DROP\_DEFAULT|The CREATE DEFAULT or DROP DEFAULT syntax was encountered. Rewrite the command by using the DEFAULT option of CREATE TABLE or ALTER TABLE. Occurs once per compilation.|  
|CREATE\_DROP\_RULE|The CREATE RULE syntax was encountered. Rewrite the command by using constraints. Occurs once per compilation.|  
|Data types: text ntext or image|A **text**, **ntext**, or **image** data types was encountered. Rewrite applications to use the **varchar\(max\)** data type and removed **text**, **ntext**, and **image** data type syntax. Occurs once per query.|  
||The total number of times a database was changed to compatibility level 80. Plan to upgrade the database and application before the next release. Also occurs when a database at compatibility level 80 is started.|  
|Database compatibility level 100, 110. 120|The total number of times a database compatibility level was changed. Plan to upgrade the database and application for a future release. Also occurs when a database at a deprecated compatibility level is started.|  
|DATABASE\_MIRRORING|References to database mirroring feature were encountered. Plan to upgrade to Always On Availability Groups, or if you are running an edition of SQL Server that does not support Always On Availability Groups, plan to migrate to log shipping.|  
|database\_principal\_aliases|References to the deprecated sys.database\_principal\_aliases were encountered. Use roles instead of aliases. Occurs once per compilation.|  
|DATABASEPROPERTY|A statement referenced DATABASEPROPERTY. Update the statement DATABASEPROPERTY to DATABASEPROPERTYEX. Occurs once per compilation.|  
|DATABASEPROPERTYEX\('IsFullTextEnabled'\)|A statement referenced the DATABASEPROPERTYEX IsFullTextEnabled property. The value of this property has no effect. User databases are always enabled for full\-text search. Do not use this property. Occurs once per compilation.|  
|DBCC \[UN\]PINTABLE|The DBCC PINTABLE or DBCC UNPINTABLE statement was encountered. This statement has no effect and should be removed. Occurs once per query.|  
|DBCC DBREINDEX|The DBCC DBREINDEX statement was encountered. Rewrite the statement to use the REBUILD option of ALTER INDEX. Occurs once per query.|  
|DBCC INDEXDEFRAG|The DBCC INDEXDEFRAG statement was encountered. Rewrite the statement to use the REORGANIZE option of ALTER INDEX. Occurs once per query.|  
|DBCC SHOWCONTIG|The DBCC SHOWCONTIG statement was encountered. Query sys.dm\_db\_index\_physical\_stats for this information. Occurs once per query.|  
|DEFAULT keyword as a default value|Syntax that uses the DEFAULT keyword as a default value was encountered. Do not use. Occurs once per compilation.|  
|Deprecated encryption algorithm|Deprecated encryption algorithm rc4 will be removed in the next version of SQL Server. Avoid using this feature in new development work, and plan to modify applications that currently use it. The RC4 algorithm is weak and is only supported for backward compatibility. New material can only be encrypted using RC4 or RC4\_128 when the database is in compatibility level 90 or 100. \(Not recommended.\) Use a newer algorithm such as one of the AES algorithms instead. In [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] and higher material encrypted using RC4 or RC4\_128 can be unencrypted in any compatibility level.|  
|Deprecated hash algorithm|Use of the MD2, MD4, MD5, SHA, or SHA1 algorithms.|  
|DESX algorithm|Syntax that uses the DESX encryption algorithm was encountered. Use another algorithm for encryption. Occurs once per compilation.|  
|dm\_fts\_active\_catalogs|The dm\_fts\_active\_catalogs counter always remains at 0 because some columns of the sys.dm\_fts\_active\_catalogs view are not deprecated. To monitor a deprecated column, use the column\-specific counter; for example, dm\_fts\_active\_catalogs.is\_paused.|  
|dm\_fts\_active\_catalogs.is\_paused|The is\_paused column of the [sys.dm\_fts\_active\_catalogs](../Topic/sys.dm_fts_active_catalogs%20\(Transact-SQL\).md) dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.previous\_status|The previous\_status column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.previous\_status\_description|The previous\_status\_description column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.row\_count\_in\_thousands|The row\_count\_in\_thousands column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.status|The status column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.status\_description|The status\_description column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_active\_catalogs.worker\_count|The worker\_count column of the sys.dm\_fts\_active\_catalogs dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|dm\_fts\_memory\_buffers|The dm\_fts\_memory\_buffers counter always remains at 0 because most columns of the sys.dm\_fts\_memory\_buffers view are not deprecated. To monitor the deprecated column, use the column\-specific counter: dm\_fts\_memory\_buffers.row\_count.|  
|dm\_fts\_memory\_buffers.row\_count|The row\_count column of the [sys.dm\_fts\_memory\_buffers](../Topic/sys.dm_fts_memory_buffers%20\(Transact-SQL\).md) dynamic management view was encountered. Avoid using this column. Occurs every time the server instance detects a reference to the column.|  
|DROP INDEX with two\-part name|The DROP INDEX syntax contained the format *table\_name.index\_name* syntax in DROP INDEX. Replace with *index\_name* ON *table\_name* syntax in the DROP INDEX statement. Occurs once per compilation.|  
|EXT\_CREATE\_ALTER\_SOAP\_ENDPOINT|The CREATE or ALTER ENDPOINT statement with the FOR SOAP option was encountered. Native XML Web Services is deprecated. Use Windows Communications Foundation \(WCF\) or ASP.NET instead.|  
|EXT\_endpoint\_webmethods|sys.endpoint\_webmethods was encountered. Native XML Web Services is deprecated. Use Windows Communications Foundation \(WCF\) or ASP.NET instead.|  
|EXT\_soap\_endpoints|sys.soap\_endpoints was encountered. Native XML Web Services is deprecated. Use Windows Communications Foundation \(WCF\) or ASP.NET instead.|  
|EXTPROP\_LEVEL0TYPE|TYPE was encountered at a level0type. Use SCHEMA as the level0type, and TYPE as the level1type. Occurs once per query.|  
|EXTPROP\_LEVEL0USER|A level0type USER when a level1type was also specified. Use USER only as a level0type for extended properties directly on a user. Occurs once per query.|  
|FASTFIRSTROW|The FASTFIRSTROW syntax was encountered. Rewrite statements to use the OPTION \(FAST *n*\) syntax. Occurs once per compilation.|  
|FILE\_ID|The FILE\_ID syntax was encountered. Rewrite statements to use FILE\_IDEX. Occurs once per compilation.|  
|fn\_get\_sql|The fn\_get\_sql function was compiled. Use sys.dm\_exec\_sql\_text instead. Occurs once per compilation.|  
|fn\_servershareddrives|The fn\_servershareddrives function was compiled. Use sys.dm\_io\_cluster\_shared\_drives instead. Occurs once per compilation.|  
|fn\_virtualservernodes|The fn\_virtualservernodes function was compiled. Use sys.dm\_os\_cluster\_nodes instead. Occurs once per compilation.|  
|fulltext\_catalogs|The fulltext\_catalogs counter always remains at 0 because some columns of the sys.fulltext\_catalogs view are not deprecated. To monitor a deprecated column, use its column\-specific counter; for example, fulltext\_catalogs.data\_space\_id. Occurs every time the server instance detects a reference to the column.|  
|fulltext\_catalogs.data\_space\_id|The data\_space\_id column of the [sys.fulltext\_catalogs](../Topic/sys.fulltext_catalogs%20\(Transact-SQL\).md) catalog view was encountered. Do not use this column. Occurs every time the server instance detects a reference to the column.|  
|fulltext\_catalogs.file\_id|The file\_id column of the sys.fulltext\_catalogs catalog view was encountered. Do not use this column. Occurs every time the server instance detects a reference to the column.|  
|fulltext\_catalogs.path|The path column of the sys.fulltext\_catalogs catalog view was encountered. Do not use this column. Occurs every time the server instance detects a reference to the column.|  
|FULLTEXTCATALOGPROPERTY\('LogSize'\)|The LogSize property of the FULLTEXTCATALOGPROPERTY function was encountered. Avoid using this property.|  
|FULLTEXTCATALOGPROPERTY\('PopulateStatus'\)|The PopulateStatus property of the FULLTEXTCATALOGPROPERTY function was encountered. Avoid using this property.|  
|FULLTEXTSERVICEPROPERTY\('ConnectTimeout'\)|The ConnectTimeout property of the FULLTEXTSERVICEPROPERTY function was encountered. Avoid using this property.|  
|FULLTEXTSERVICEPROPERTY\('DataTimeout'\)|The DataTimeout property of the FULLTEXTSERVICEPROPERTY function was encountered. Avoid using this property.|  
|FULLTEXTSERVICEPROPERTY\('ResourceUsage'\)|The ResourceUsage property of the FULLTEXTSERVICEPROPERTY function was encountered. Avoid using this property.|  
|GROUP BY ALL|Total number of times the GROUP BY ALL syntax was encountered. Modify the syntax to group by specific tables.|  
|Hindi|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation. Use Indic\_General\_90 instead.|  
|HOLDLOCK table hint without parentheses||  
|IDENTITYCOL|The INDENTITYCOL syntax was encountered. Rewrite statements to use the $identity syntax. Occurs once per compilation.|  
|Index view select list without COUNT\_BIG\(\*\)|The select list of an aggregate indexed view must contain COUNT\_BIG \(\*\) .|  
|INDEX\_OPTION|Encountered CREATE TABLE, ALTER TABLE, or CREATE INDEX syntax without parentheses around the options. Rewrite the statement to use the current syntax. Occurs once per query.|  
|INDEXKEY\_PROPERTY|The INDEXKEY\_PROPERTY syntax was encountered. Rewrite statements to query sys.index\_columns. Occurs once per compilation.|  
|Indirect TVF hints|The indirect application, through a view, of table hints to an invocation of a multistatement table\-valued function \(TVF\) will be removed in a future version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|INSERT NULL into TIMESTAMP columns|A NULL value was inserted to a TIMESTAMP column. Use a default value instead. Occurs once per compilation.|  
|INSERT\_HINTS||  
|Korean\_Wansung\_Unicode|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation.|  
|Lithuanian\_Classic|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation.|  
|Macedonian|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation. Use Macedonian\_FYROM\_90 instead.|  
|MODIFY FILEGROUP READONLY|The MODIFY FILEGROUP READONLY syntax was encountered. Rewrite statements to use the READ\_ONLY syntax. Occurs once per compilation.|  
|MODIFY FILEGROUP READWRITE|The MODIFY FILEGROUP READWRITE syntax was encountered. Rewrite statements to use the READ\_WRITE syntax. Occurs once per compilation.|  
|More than two\-part column name|A query used a 3\-part or 4\-part name in the column list. Change the query to use the standard\-compliant 2\-part names. Occurs once per compilation.|  
|Multiple table hints without comma|A space was used as the separator between table hints. Use a comma instead. Occurs once per compilation.|  
|NOLOCK or READUNCOMMITTED in UPDATE or DELETE|NOLOCK or READUNCOMMITTED was encountered in the FROM clause of an UPDATE or DELETE statement. Remove the NOLOCK or READUNCOMMITTED table hints from the FROM clause.|  
|Non\-ANSI \*\= or \=\* outer join operators|A statement that uses the \*\= or \=\* join syntax was encountered. Rewrite the statement to use the ANSI join syntax. Occurs once per compilation.|  
|numbered\_stored\_procedures||  
|numbered\_procedure\_parameters|References to the deprecated sys.numbered\_procedure\_parameters were encountered. Do not use. Occurs once per compilation.|  
|numbered\_procedures|References to the deprecated sys.numbered\_procedures were encountered. Do not use. Occurs once per compilation.|  
|Oldstyle RAISEERROR|The deprecated RAISERROR \(Format: RAISERROR integer string\) syntax was encountered. Rewrite the statement using the current RAISERROR syntax. Occurs once per compilation.|  
|OLEDB for ad hoc connections|SQLOLEDB is not a supported provider. Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client for ad hoc connections.|  
|PERMISSIONS|References to the PERMISSIONS intrinsic function were encountered. Query sys.fn\_my\_permissions instead. Occurs once per query.|  
|ProcNums|The deprecated ProcNums syntax was encountered. Rewrite statements to remove the references. Occurs once per compilation.|  
|READTEXT|The READTEXT syntax was encountered. Rewrite applications to use the **varchar\(max\)** data type and removed **text** data type syntax. Occurs once per query.|  
|RESTORE DATABASE or LOG WITH DBO\_ONLY|The RESTORE … WITH DBO\_ONLY syntax was encountered. Use RESTORE … RESTRICTED\_USER instead.|  
|RESTORE DATABASE or LOG WITH MEDIAPASSWORD|The RESTORE … WITH MEDIAPASSWORD syntax was encountered. WITH MEDIAPASSWORD provides weak security and should be removed.|  
|RESTORE DATABASE or LOG WITH PASSWORD|The RESTORE … WITH PASSWORD syntax was encountered. WITH PASSWORD provides weak security and should be removed.|  
|Returning results from trigger|This event occurs once per trigger invocation. Rewrite the trigger so that it does not return result sets.|  
|ROWGUIDCOL|The ROWGUIDCOL syntax was encountered. Rewrite statements to use the $rowguid syntax. Occurs once per compilation.|  
|SET ANSI\_NULLS OFF|The SET ANSI\_NULLS OFF syntax was encountered. Remove this deprecated syntax. Occurs once per compilation.|  
|SET ANSI\_PADDING OFF|The SET ANSI\_PADDING OFF syntax was encountered. Remove this deprecated syntax. Occurs once per compilation.|  
|SET CONCAT\_NULL\_YIELDS\_NULL OFF|The SET CONCAT\_NULL\_YIELDS\_NULL OFF syntax was encountered. Remove this deprecated syntax. Occurs once per compilation.|  
|SET DISABLE\_DEF\_CNST\_CHK|The SET DISABLE\_DEF\_CNST\_CHK syntax was encountered. This has no effect. Remove this deprecated syntax. Occurs once per compilation.|  
|SET FMTONLY ON|The SET FMTONLY syntax was encountered. Remove this deprecated syntax. Occurs once per compilation.|  
|SET OFFSETS|The SET OFFSETS syntax was encountered. Remove this deprecated syntax. Occurs once per compilation.|  
|SET REMOTE\_PROC\_TRANSACTIONS|The SET REMOTE\_PROC\_TRANSACTIONS syntax was encountered. Remove this deprecated syntax. Use linked servers and sp\_serveroption instead.|  
|SET ROWCOUNT|The SET ROWCOUNT syntax was encountered in a DELETE, INSERT, or UPDATE statement. Rewrite the statement by using TOP. Occurs once per compilation.|  
|SETUSER|The SET USER statement was encountered. Use EXECUTE AS instead. Occurs once per query.|  
|sp\_addapprole|The sp\_addapprole procedure was encountered. Use CREATE APPLICATION ROLE instead. Occurs once per query.|  
|sp\_addextendedproc|The sp\_addextendedproc procedure was encountered. Use CLR instead. Occurs once per compilation.|  
|sp\_addlogin|The sp\_addlogin procedure was encountered. Use CREATE LOGIN instead. Occurs once per query.|  
|sp\_addremotelogin|The sp\_addremotelogin procedure was encountered. Use linked servers instead.|  
|sp\_addrole|The sp\_addrole procedure was encountered. Use CREATE ROLE instead. Occurs once per query.|  
|sp\_addserver|The sp\_addserver procedure was encountered. Use linked servers instead.|  
|sp\_addtype|The sp\_addtype procedure was encountered. Use CREATE TYPE instead. Occurs once per compilation.|  
|sp\_adduser|The sp\_adduser procedure was encountered. Use CREATE USER instead. Occurs once per query.|  
|sp\_approlepassword|The sp\_approlepassword procedure was encountered. Use ALTER APPLICATION ROLE instead. Occurs once per query.|  
|sp\_attach\_db|The sp\_attach\_db procedure was encountered. Use CREATE DATABASE FOR ATTACH instead. Occurs once per query.|  
|sp\_attach\_single\_file\_db|The sp\_single\_file\_db procedure was encountered. Use CREATE DATABASE FOR ATTACH\_REBUILD\_LOG instead. Occurs once per query.|  
|sp\_bindefault|The sp\_bindefault procedure was encountered. Use the DEFAULT keyword of ALTER TABLE or CREATE TABLE instead. Occurs once per compilation.|  
|sp\_bindrule|The sp\_bindrule procedure was encountered. Use check constraints instead. Occurs once per compilation.|  
|sp\_bindsession|The sp\_bindsession procedure was encountered. Use Multiple Active Result Sets \(MARS\) or distributed transactions instead. Occurs once per compilation.|  
|sp\_certify\_removable|The sp\_certify\_removable procedure was encountered. Use sp\_detach\_db instead. Occurs once per query.|  
|sp\_changeobjectowner|The sp\_changeobjectowner procedure was encountered. Use ALTER SCHEMA or ALTER AUTHORIZATION instead. Occurs once per query.|  
|sp\_change\_users\_login|The sp\_change\_users\_login procedure was encountered. Use ALTER USER instead. Occurs once per query.|  
|sp\_configure 'allow updates'|The allow updates option of sp\_configure was encountered. System tables are no longer updatable. Do not use. Occurs once per query.|  
|sp\_configure 'disallow results from triggers'|The disallow result sets from triggers option of sp\_configure was encountered. To disallow result sets from triggers, use sp\_configure to set the option to 1. Occurs once per query.|  
|sp\_configure 'ft crawl bandwidth \(max\)'|The ft crawl bandwidth \(max\) option of sp\_configure was encountered. Do not use. Occurs once per query.|  
|sp\_configure 'ft crawl bandwidth \(min\)'|The ft crawl bandwidth \(min\) option of sp\_configure was encountered. Do not use. Occurs once per query.|  
|sp\_configure 'ft notify bandwidth \(max\)'|The ft notify bandwidth \(max\) option of sp\_configure was encountered. Do not use. Occurs once per query.|  
|sp\_configure 'ft notify bandwidth \(min\)'|The ft notify bandwidth \(min\) option of sp\_configure was encountered. Do not use. Occurs once per query.|  
|sp\_configure 'locks'|The locks option of sp\_configure was encountered. Locks are no longer configurable. Do not use. Occurs once per query.|  
|sp\_configure 'open objects'|The open objects option of sp\_configure was encountered. The number of open objects is no longer configurable. Do not use. Occurs once per query.|  
|sp\_configure 'priority boost'|The priority boost option of sp\_configure was encountered. Do not use. Occurs once per query. Use the Windows start \/high … program.exe option instead.|  
|sp\_configure 'remote proc trans'|The remote proc trans option of sp\_configure was encountered. Do not use. Occurs once per query.|  
|sp\_configure 'set working set size'|The set working set size option of sp\_configure was encountered. The working set size is no longer configurable. Do not use. Occurs once per query.|  
|sp\_control\_dbmasterkey\_password|The sp\_control\_dbmasterkey\_password stored procedure does not check whether a master key exists. This is permitted for backward compatibility, but displays a warning. This behavior is deprecated. In a future release the master key must exist and the password used in the stored procedure sp\_control\_dbmasterkey\_password must be the same password as one of the passwords used to encrypt the database master key.|  
|sp\_create\_removable|The sp\_create\_removable procedure was encountered. Use CREATE DATABASE instead. Occurs once per query.|  
|sp\_db\_vardecimal\_storage\_format|Use of **vardecimal** storage format was encountered. Use data compression instead.|  
|sp\_dbcmptlevel|The sp\_dbcmptlevel procedure was encountered. Use ALTER DATABASE … SET COMPATIBILITY\_LEVEL instead. Occurs once per query.|  
|sp\_dbfixedrolepermission|The sp\_dbfixedrolepermission procedure was encountered. Do not use. Occurs once per query.|  
|sp\_dboption|The sp\_dboption procedure was encountered. Use ALTER DATABASE and DATABASEPROPERTYEX instead. Occurs once per compilation.|  
|sp\_dbremove|The sp\_dbremove procedure was encountered. Use DROP DATABASE instead. Occurs once per query.|  
|sp\_defaultdb|The sp\_defaultdb procedure was encountered. Use ALTER LOGIN instead. Occurs once per compilation.|  
|sp\_defaultlanguage|The sp\_defaultlanguage procedure was encountered. Use ALTER LOGIN instead. Occurs once per compilation.|  
|sp\_denylogin|The sp\_denylogin procedure was encountered. Use ALTER LOGIN DISABLE instead. Occurs once per query.|  
|sp\_depends|The sp\_depends procedure was encountered. Use sys.dm\_sql\_referencing\_entities and sys.dm\_sql\_referenced\_entities instead. Occurs once per query.|  
|sp\_detach\_db @keepfulltextindexfile|The @keepfulltextindexfile argument was encountered in a sp\_detach\_db statement. Do not use this argument.|  
|sp\_dropalias|The sp\_dropalias procedure was encountered. Replace aliases with a combination of user accounts and database roles. Use sp\_dropalias to remove aliases in upgraded databases. Occurs once per compilation.|  
|sp\_dropapprole|The sp\_dropapprole procedure was encountered. Use DROP APPLICATION ROLE instead. Occurs once per query.|  
|sp\_dropextendedproc|The sp\_dropextendedproc procedure was encountered. Use CLR instead. Occurs once per compilation.|  
|sp\_droplogin|The sp\_droplogin procedure was encountered. Use DROP LOGIN instead. Occurs once per query.|  
|sp\_dropremotelogin|The sp\_dropremotelogin procedure was encountered. Use linked servers instead.|  
|sp\_droprole|The sp\_droprole procedure was encountered. Use DROP ROLE instead. Occurs once per query.|  
|sp\_droptype|The sp\_droptype procedure was encountered. Use DROP TYPE instead.|  
|sp\_dropuser|The sp\_dropuser procedure was encountered. Use DROP USER instead. Occurs once per query.|  
|sp\_estimated\_rowsize\_reduction\_for\_vardecimal|Use of **vardecimal** storage format was encountered. Use data compression and sp\_estimate\_data\_compression\_savings instead.|  
|sp\_fulltext\_catalog|The sp\_fulltext\_catalog procedure was encountered. Use CREATE\/ALTER\/DROP FULLTEXT CATALOG instead. Occurs once per compilation.|  
|sp\_fulltext\_column|The sp\_fulltext\_column procedure was encountered. Use ALTER FULLTEXT INDEX instead. Occurs once per compilation.|  
|sp\_fulltext\_database|The sp\_fulltext\_database procedure was encountered. Use ALTER DATABASE instead. Occurs once per compilation.|  
|sp\_fulltext\_service @action\=clean\_up|The clean\_up option of the sp\_fulltext\_service procedure was encountered. Occurs once per query.|  
|sp\_fulltext\_service @action\=connect\_timeout|The connect\_timeout option of the sp\_fulltext\_service procedure was encountered. Occurs once per query.|  
|sp\_fulltext\_service @action\=data\_timeout|The data\_timeout option of the sp\_fulltext\_service procedure was encountered. Occurs once per query.|  
|sp\_fulltext\_service @action\=resource\_usage|The resource\_usage option of the sp\_fulltext\_service procedure was encountered. This option has no function. Occurs once per query.|  
|sp\_fulltext\_table|The sp\_fulltext\_table procedure was encountered. Use CREATE\/ALTER\/DROP FULLTEXT INDEX instead. Occurs once per compilation.|  
|sp\_getbindtoken|The sp\_getbindtoken procedure was encountered. Use Multiple Active Result Sets \(MARS\) or distributed transactions instead. Occurs once per compilation.|  
|sp\_grantdbaccess|The sp\_grantdbaccess procedure was encountered. Use CREATE USER instead. Occurs once per query.|  
|sp\_grantlogin|The sp\_grantlogin procedure was encountered. Use CREATE LOGIN instead. Occurs once per query.|  
|sp\_help\_fulltext\_catalog\_components|The sp\_help\_fulltext\_catalog\_components procedure was encountered. This procedure returns empty rows. Do not use this procedure. Occurs once per compilation.|  
|sp\_help\_fulltext\_catalogs|The sp\_help\_fulltext\_catalogs procedure was encountered. Query sys.fulltext\_catalogs instead. Occurs once per compilation.|  
|sp\_help\_fulltext\_catalogs\_cursor|The sp\_help\_fulltext\_catalogs\_cursor procedure was encountered. Query sys.fulltext\_catalogs instead. Occurs once per compilation.|  
|sp\_help\_fulltext\_columns|The sp\_help\_fulltext\_columns procedure was encountered. Query sys.fulltext\_index\_columns instead. Occurs once per compilation.|  
|sp\_help\_fulltext\_columns\_cursor|The sp\_help\_fulltext\_columns\_cursor procedure was encountered. Query sys.fulltext\_index\_columns instead. Occurs once per compilation.|  
|sp\_help\_fulltext\_tables|The sp\_help\_fulltext\_tables procedure was encountered. Query sys.fulltext\_indexes instead. Occurs once per compilation.|  
|sp\_help\_fulltext\_tables\_cursor|The sp\_help\_fulltext\_tables\_cursor procedure was encountered. Query sys.fulltext\_indexes instead. Occurs once per compilation.|  
|sp\_helpdevice|The sp\_helpdevice procedure was encountered. Query sys.backup\_devices instead. Occurs once per query.|  
|sp\_helpextendedproc|The sp\_helpextendedproc procedure was encountered. Use CLR instead. Occurs once per compilation.|  
|sp\_helpremotelogin|The sp\_helpremotelogin procedure was encountered. Use linked servers instead.|  
|sp\_indexoption|The sp\_indexoption procedure was encountered. Use ALTER INDEX instead. Occurs once per compilation.|  
|sp\_lock|The sp\_lock procedure was encountered. Query sys.dm\_tran\_locks instead. Occurs once per query.|  
|sp\_password|The sp\_password procedure was encountered. Use ALTER LOGIN instead. Occurs once per query.|  
|sp\_remoteoption|The sp\_remoteoption procedure was encountered. Use linked servers instead.|  
|sp\_renamedb|The sp\_renamedb procedure was encountered. Use ALTER DATABASE instead. Occurs once per query.|  
|sp\_resetstatus|The sp\_resetstatus procedure was encountered. Use ALTER DATABASE instead. Occurs once per query.|  
|sp\_revokedbaccess|The sp\_revokedbaccess procedure was encountered. Use DROP USER instead. Occurs once per query.|  
|sp\_revokelogin|The sp\_revokelogin procedure was encountered. Use DROP LOGIN instead. Occurs once per query.|  
|sp\_srvrolepermission|The deprecated sp\_srvrolepermission procedure was encountered. Do not use. Occurs once per query.|  
|sp\_unbindefault|The sp\_unbindefault procedure was encountered. Use the DEFAULT keyword in CREATE TABLE or ALTER TABLE statements instead. Occurs once per compilation.|  
|sp\_unbindrule|The sp\_unbindrule procedure was encountered. Use check constraints instead of rules. Occurs once per compilation.|  
|SQL\_AltDiction\_CP1253\_CS\_AS|Event occurs once per database start and once per collation use. Plan to modify applications that use this collation.|  
|String literals as column aliases|Syntax that contains a string that is used as a column alias in a SELECT statement, such as `'string' = expression`, was encountered. Do not use. Occurs once per compilation.|  
|sys.sql\_dependencies|References to sys.sql\_dependencies were encountered. Use sys.sql\_expression\_dependencies instead. Occurs once per compilation.|  
|sysaltfiles|References to sysaltfiles were encountered. Use sys.master\_files instead. Occurs once per compilation.|  
|syscacheobjects|References to syscacheobjects were encountered. Use sys.dm\_exec\_cached\_plans, sys.dm\_exec\_plan\_attributes, and sys.dm\_exec\_sql\_text instead. Occurs once per compilation.|  
|syscolumns|References to syscolumns were encountered. Use sys.columns instead. Occurs once per compilation.|  
|syscomments|References to syscomments were encountered. Use sys.sql\_modules instead. Occurs once per compilation.|  
|sysconfigures|References to the sysconfigures table were encountered. Reference the sys.sysconfigures view instead. Occurs once per compilation.|  
|sysconstraints|References to sysconstraints were encountered Use sys.check\_constraints, sys.default\_constraints, sys.key\_constraints, sys.foreign\_keys instead. Occurs once per compilation.|  
|syscurconfigs|References to syscurconfigs were encountered. Use sys.configurations instead. Occurs once per compilation.|  
|sysdatabases|References to sysdatabases were encountered. Use sys.databases instead. Occurs once per compilation.|  
|sysdepends|References to sysdepends were encountered. Use sys.sql\_dependencies instead. Occurs once per compilation.|  
|sysdevices|References to sysdevices were encountered. Use sys.backup\_devices instead. Occurs once per compilation.|  
|sysfilegroups|References to sysfilegroups were encountered. Use sys.filegroups instead. Occurs once per compilation.|  
|sysfiles|References to sysfiles were encountered. Use sys.database\_files instead. Occurs once per compilation.|  
|sysforeignkeys|References to sysforeignkeys were encountered. Use sys.foreign\_keys instead. Occurs once per compilation.|  
|sysfulltextcatalogs|References to sysfulltextcatalogs were encountered. Use sys.fulltext\_catalogs instead. Occurs once per compilation.|  
|sysindexes|References to sysindexes were encountered. Use sys.indexes, sys.partitions, sys.allocation\_units, and sys.dm\_db\_partition\_stats instead. Occurs once per compilation.|  
|sysindexkeys|References to sysindexkeys were encountered. Use sys.index\_columns instead. Occurs once per compilation.|  
|syslockinfo|References to syslockinfo were encountered. Use sys.dm\_tran\_locks instead. Occurs once per compilation.|  
|syslogins|References to syslogins were encountered. Use sys.server\_principals and sys.sql\_logins instead. Occurs once per compilation.|  
|sysmembers|References to sysmembers were encountered. Use sys.database\_role\_members instead. Occurs once per compilation.|  
|sysmessages|References to sysmessages were encountered. Use sys.messages instead. Occurs once per compilation.|  
|sysobjects|References to sysobjects were encountered. Use sys.objects instead. Occurs once per compilation.|  
|sysoledbusers|References to sysoledbusers were encountered. Use sys.linked\_logins instead. Occurs once per compilation.|  
|sysopentapes|References to sysopentapes were encountered. Use sys.dm\_io\_backup\_tapes instead. Occurs once per compilation.|  
|sysperfinfo|References to sysperfinfo were encountered. Use sys.dm\_os\_performance\_counters. instead. Occurs once per compilation.|  
|syspermissions|References to syspermissions were encountered. Use sys.database\_permissions and sys.server\_permissions instead. Occurs once per compilation.|  
|sysprocesses|References to sysprocesses were encountered. Use sys.dm\_exec\_connections, sys.dm\_exec\_sessions, and sys.dm\_exec\_requests instead. Occurs once per compilation.|  
|sysprotects|References to sysprotects were encountered. Use sys.database\_permissions and sys.server\_permissions instead. Occurs once per compilation.|  
|sysreferences|References to sysreferences were encountered. Use sys.foreign\_keys instead. Occurs once per compilation.|  
|sysremotelogins|References to sysremotelogins were encountered. Use sys.remote\_logins instead. Occurs once per compilation.|  
|sysservers|References to sysservers were encountered. Use sys.servers instead. Occurs once per compilation.|  
|systypes|References to systypes were encountered. Use sys.types instead. Occurs once per compilation.|  
|sysusers|References to sysusers were encountered. Use sys.database\_principals instead. Occurs once per compilation.|  
|Table hint without WITH|A statement that used table hints but did not use the WITH keyword was encountered. Modify statements to include the word WITH. Occurs once per compilation.|  
|Text in row table option|References to the 'text in row' table option were encountered. Use sp\_tableoption 'large value types out of row' instead. Occurs once per query.|  
|TEXTPTR|References to the TEXTPTR function were encountered. Rewrite applications to use the **varchar\(max\)** data type and removed **text**, **ntext**, and **image** data type syntax. Occurs once per query.|  
|TEXTVALID|References to the TEXTVALID function were encountered. Rewrite applications to use the **varchar\(max\)** data type and removed **text**, **ntext**, and **image** data type syntax. Occurs once per query.|  
|TIMESTAMP|Total number of times the deprecated **timestamp** data type was encountered in a DDL statement. Use the **rowversion** data type instead.|  
|UPDATETEXT or WRITETEXT|The UPDATETEXT or WRITETEXT statement was encountered. Rewrite applications to use the **varchar\(max\)** data type and removed **text**, **ntext**, and **image** data type syntax. Occurs once per query.|  
|USER\_ID|References to the USER\_ID function were encountered. Use the DATABASE\_PRINCIPAL\_ID function instead. Occurs once per compilation.|  
|Using OLEDB for linked servers||  
|Vardecimal storage format|Use of **vardecimal** storage format was encountered. Use data compression instead.|  
|XMLDATA|The FOR XML syntax was encountered. Use XSD generation for RAW and AUTO modes. There is no replacement for the explicit mode. Occurs once per compilation.|  
|XP\_API|An extended stored procedure statement was encountered. Do not use.|  
|xp\_grantlogin|The xp\_grantlogin procedure was encountered. Use CREATE LOGIN instead. Occurs once per compilation.|  
|xp\_loginconfig|The xp\_loginconfig procedure was encountered. Use the IsIntegratedSecurityOnly argument of SERVERPROPERTY instead. Occurs once per query.|  
|xp\_revokelogin|The xp\_revokelogin procedure was encountered. Use ALTER LOGIN DISABLE or DROP LOGIN instead. Occurs once per compilation.|  
  
## See Also  
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)   
 [Deprecated Full-Text Search Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Deprecated-Full-Text-Search-Features-in-SQL-Server-2016.md)   
 [Deprecation Announcement Event Class](../../Topics\TopicNameNotContainA/Deprecation-Announcement-Event-Class.md)   
 [Deprecation Final Support Event Class](../../Topics\TopicNameNotContainA/Deprecation-Final-Support-Event-Class.md)   
 [Discontinued Database Engine Functionality in SQL Server 2016](../../Topics\TopicNameNotContainA/Discontinued-Database-Engine-Functionality-in-SQL-Server-2016.md)   
 [Discontinued Full-Text Search Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Discontinued-Full-Text-Search-Features-in-SQL-Server-2016.md)   
 [Use SQL Server Objects](../../Topics\TopicNameNotContainA/Use-SQL-Server-Objects.md)  
  
  