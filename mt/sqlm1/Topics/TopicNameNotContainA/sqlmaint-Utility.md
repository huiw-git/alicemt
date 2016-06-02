---
title: sqlmaint Utility
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 937a9932-4aed-464b-b97a-a5acfe6a50de
---
# sqlmaint Utility
  The**sqlmaint** utility performs a specified set of maintenance operations on one or more databases. Use **sqlmaint** to run DBCC checks, back up a database and its transaction log, update statistics, and rebuild indexes. All database maintenance activities generate a report that can be sent to a designated text file, HTML file, or e\-mail account. **sqlmaint** executes database maintenance plans created with previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. To run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] maintenance plans from the command prompt, use the [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../Token\Other/ssNoteDepNextAvoid_md.md)] Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] maintenance plan feature instead. For more information on maintenance plans, see [Maintenance Plans](../../Topics\TopicNameNotContainA/Maintenance-Plans.md).  
  
## Syntax  
  
```  
  
sqlmaint   
[-?] |  
[  
     [-S server_name[\instance_name]]  
     [-U login_ID [-P password]]  
     {  
          [-D database_name | -PlanName name | -PlanID guid ]  
          [-Rpt text_file]  
          [-To operator_name]  
          [-HtmlRpt html_file [-DelHtmlRpt <time_period>] ]  
          [-RmUnusedSpace threshold_percentfree_percent]  
          [-CkDB | -CkDBNoIdx]  
          [-CkAl | -CkAlNoIdx]  
          [-CkCat]  
          [-UpdOptiStats sample_percent]  
          [-RebldIdx free_space]  
          [-SupportComputedColumn]  
          [-WriteHistory]  
          [  
               {-BkUpDB [backup_path] | -BkUpLog [backup_path] }  
               {-BkUpMedia  
                    {DISK [  
                           [-DelBkUps <time_period>]   
                           [-CrBkSubDir ]   
                           [-UseDefDir ]   
                          ]  
                     | TAPE   
                    }  
               }  
               [-BkUpOnlyIfClean]  
               [-VrfyBackup]  
          ]  
     }  
]  
<time_period> ::=  
number[minutes | hours | days | weeks | months]  
```  
  
## Arguments  
 The parameters and their values must be separated by a space. For example, there must be a space between **\-S** and *server\_name*.  
  
 **\-?**  
 Specifies that the syntax diagram for **sqlmaint** be returned. This parameter must be used alone.  
  
 **\-S** *server\_name*\[ **\\***instance\_name*\]  
 Specifies the target instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Specify *server\_name* to connect to the default instance of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] on that server. Specify *server\_name***\\***instance\_name* to connect to a named instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on that server. If no server is specified, **sqlmaint** connects to the default instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on the local computer.  
  
 **\-U** *login\_ID*  
 Specifies the login ID to use when connecting to the server. If not supplied, **sqlmaint** attempts to use [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Authentication. If *login\_ID* contains special characters, it must be enclosed in double quotation marks \("\); otherwise, the double quotation marks are optional.  
  
> [!IMPORTANT]  
>  When possible, use Windows Authentication.  
  
 **\-P** *password*  
 Specifies the password for the login ID. Only valid if the **\-U** parameter is also supplied. If *password* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.  
  
> [!IMPORTANT]  
>  The password is not masked. When possible, use Windows Authentication.  
  
 **\-D** *database\_name*  
 Specifies the name of the database in which to perform the maintenance operation. If *database\_name* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.  
  
 **\-PlanName** *name*  
 Specifies the name of a database maintenance plan defined using the Database Maintenance Plan Wizard. The only information **sqlmaint** uses from the plan is the list of the databases in the plan. Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.  
  
 **\-PlanID** *guid*  
 Specifies the globally unique identifier \(GUID\) of a database maintenance plan defined using the Database Maintenance Plan Wizard. The only information **sqlmaint** uses from the plan is the list of the databases in the plan. Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases. This must match a plan\_id value in msdb.dbo.sysdbmaintplans.  
  
 **\-Rpt** *text\_file*  
 Specifies the full path and name of the file into which the report is to be generated. The report is also generated on the screen. The report maintains version information by adding a date to the file name. The date is generated as follows: at the end of the file name but before the period, in the form \_*yyyyMMddhhmm*. *yyyy* \= year, *MM* \= month, *dd* \= day, *hh* \= hour, *mm* \= minute.  
  
 If you run the utility at 10:23 A.M. on December 1, 1996, and this is the *text\_file* value:  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.rpt  
```  
  
 The generated file name is:  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint_199612011023.rpt  
```  
  
 The full Universal Naming Convention \(UNC\) file name is required for *text\_file* when **sqlmaint** accesses a remote server.  
  
 **\-To**  *operator\_name*  
 Specifies the operator to whom the generated report is sent through SQL Mail.  
  
 **\-HtmlRpt** *html\_file*  
 Specifies the full path and name of the file into which an HTML report is to be generated. **sqlmaint** generates the file name by appending a string of the format \_*yyyyMMddhhmm* to the file name, just as it does for the **\-Rpt** parameter.  
  
 The full UNC file name is required for *html\_file* when **sqlmaint** accesses a remote server.  
  
 **\-DelHtmlRpt** \<*time\_period*\>  
 Specifies that any HTML report in the report directory be deleted if the time interval after the creation of the report file exceeds \<*time\_period*\>. **\-DelHtmlRpt** looks for files whose name fits the pattern generated from the *html\_file* parameter. If *html\_file* is c:\\Program Files\\Microsoft SQL Server\\Mssql\\Backup\\AdventureWorks2012\_maint.htm, then **\-DelHtmlRpt** causes **sqlmaint** to delete any files whose names match the pattern C:\\Program Files\\Microsoft SQL Server\\Mssql\\Backup\\AdventureWorks2012\_maint\*.htm and that are older than the specified \<*time\_period*\>.  
  
 **\-RmUnusedSpace** *threshold\_percent free\_percent*  
 Specifies that unused space be removed from the database specified in **\-D**. This option is only useful for databases that are defined to grow automatically. *Threshold\_percent* specifies in megabytes the size that the database must reach before **sqlmaint** attempts to remove unused data space. If the database is smaller than the *threshold\_percent*, no action is taken. *Free\_percent* specifies how much unused space must remain in the database, specified as a percentage of the final size of the database. For example, if a 200\-MB database contains 100 MB of data, specifying 10 for *free\_percent* results in the final database size being 110 MB. Note that a database is not expanded if it is smaller than *free\_percent* plus the amount of data in the database. For example, if a 108\-MB database has 100 MB of data, specifying 10 for *free\_percent* does not expand the database to 110 MB; it remains at 108 MB.  
  
 **\-CkDB** | **\-CkDBNoIdx**  
 Specifies that a DBCC CHECKDB statement or a DBCC CHECKDB statement with the NOINDEX option be run in the database specified in **\-D**. For more information, see DBCC CHECKDB.  
  
 A warning is written to *text\_file* if the database is in use when **sqlmaint** runs.  
  
 **\-CkAl** | **\-CkAlNoIdx**  
 Specifies that a DBCC CHECKALLOC statement with the NOINDEX option be run in the database specified in **\-D**. For more information, see [DBCC CHECKALLOC &#40;Transact-SQL&#41;](../Topic/DBCC%20CHECKALLOC%20\(Transact-SQL\).md).  
  
 **\-CkCat**  
 Specifies that a DBCC CHECKCATALOG \(Transact\-SQL\) statement be run in the database specified in **\-D**. For more information, see [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](../Topic/DBCC%20CHECKCATALOG%20\(Transact-SQL\).md).  
  
 **\-UpdOptiStats** *sample\_percent*  
 Specifies that the following statement be run on each table in the database:  
  
```  
UPDATE STATISTICS table WITH SAMPLE sample_percent PERCENT;  
```  
  
 If the tables contain computed columns, you must also specify the **\-SupportedComputedColumn** argument when you use **\-UpdOptiStats**.  
  
 For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](../Topic/UPDATE%20STATISTICS%20\(Transact-SQL\).md).  
  
 **\-RebldIdx** *free\_space*  
 Specifies that indexes on tables in the target database should be rebuilt by using the *free\_space* percent value as the inverse of the fill factor. For example, if *free\_space* percentage is 30, then the fill factor used is 70. If a *free\_space* percentage value of 100 is specified, then the indexes are rebuilt with the original fill factor value.  
  
 If the indexes are on computed columns, you must also specify the **\-SupportComputedColumn** argument when you use **\-RebldIdx**.  
  
 **\-SupportComputedColumn**  
 Must be specified to run DBCC maintenance commands with **sqlmaint** on computed columns.  
  
 **\-WriteHistory**  
 Specifies that an entry be made in msdb.dbo.sysdbmaintplan\_history for each maintenance action performed by **sqlmaint**. If **\-PlanName** or **\-PlanID** is specified, the entries in sysdbmaintplan\_history use the ID of the specified plan. If **\-D** is specified, the entries in sysdbmaintplan\_history are made with zeroes for the plan ID.  
  
 **\-BkUpDB** \[ *backup\_path*\] |  **\-BkUpLog** \[ *backup\_path* \]  
 Specifies a backup action. **\-BkUpDb** backs up the entire database. **\-BkUpLog** backs up only the transaction log.  
  
 *backup\_path* specifies the directory for the backup. *backup\_path* is not needed if **\-UseDefDir** is also specified, and is overridden by **\-UseDefDir** if both are specified. The backup can be placed in a directory or a tape device address \(for example, \\\\.\\TAPE0\). The file name for a database backup is generated automatically as follows:  
  
```  
dbname_db_yyyyMMddhhmm.BAK  
  
```  
  
 where  
  
-   *dbname* is the name of the database being backed up.  
  
-   *yyyyMMddhhmm* is the time of the backup operation with *yyyy* \= year, *MM* \= month, *dd* \= day, *hh* \= hour, and *mm* \= minute.  
  
 The file name for a transaction backup is generated automatically with a similar format:  
  
```  
dbname_log_yyyymmddhhmm.BAK  
  
```  
  
 If you use the **\-BkUpDB** parameter, you must also specify the media by using the **\-BkUpMedia** parameter.  
  
 **\-BkUpMedia**  
 Specifies the media type of the backup, either DISK or TAPE.  
  
 **DISK**  
 Specifies that the backup medium is disk.  
  
 **\-DelBkUps**\< *time\_period* \>  
 For disk backups, specifies that any backup file in the backup directory be deleted if the time interval after the creation of the backup exceeds the \<*time\_period*\>.  
  
 **\-CrBkSubDir**  
 For disk backups, specifies that a subdirectory be created in the \[*backup\_path*\] directory or in the default backup directory if **\-UseDefDir** is also specified. The name of the subdirectory is generated from the database name specified in **\-D**. **\-CrBkSubDir** offers an easy way to put all the backups for different databases into separate subdirectories without having to change the *backup\_path* parameter.  
  
 **\-UseDefDir**  
 For disk backups, specifies that the backup file be created in the default backup directory. **UseDefDir** overrides *backup\_path* if both are specified. With a default [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup, the default backup directory is C:\\Program Files\\Microsoft SQL Server\\MSSQL10\_50.MSSQLSERVER\\MSSQL\\Backup.  
  
 **TAPE**  
 Specifies that the backup medium is tape.  
  
 **\-BkUpOnlyIfClean**  
 Specifies that the backup occur only if any specified **\-Ck** checks did not find problems with the data. Maintenance actions run in the same sequence as they appear in the command prompt. Specify the parameters **\-CkDB**, **\-CkDBNoIdx**, **\-CkAl**, **\-CkAlNoIdx**, **\-CkTxtAl**, or **\-CkCat** before the **\-BkUpDB**\/**\-BkUpLog** parameter\(s\) if you are also going to specify **\-BkUpOnlyIfClean**, or the backup occurs whether or not the check reports problems.  
  
 **\-VrfyBackup**  
 Specifies that RESTORE VERIFYONLY be run on the backup when it completes.  
  
 *number*\[**minutes**| **hours**| **day**| **weeks**| **months**\]  
 Specifies the time interval used to determine if a report or backup file is old enough to be deleted. *number* is an integer followed \(without a space\) by a unit of time. Valid examples:  
  
-   **12weeks**  
  
-   **3months**  
  
-   **15days**  
  
 If only *number* is specified, the default date part is **weeks**.  
  
## Remarks  
 The **sqlmaint** utility performs maintenance operations on one or more databases. If **\-D** is specified, the operations specified in the remaining switches are performed only on the specified database. If **\-PlanName** or **\-PlanID** are specified, the only information **sqlmaint** retrieves from the specified maintenance plan is the list of databases in the plan. All operations specified in the remaining **sqlmaint** parameters are applied against each database in the list obtained from the plan. The **sqlmaint** utility does not apply any of the maintenance activities defined in the plan itself.  
  
 The **sqlmaint** utility returns 0 if it runs successfully or 1 if it fails. Failure is reported:  
  
-   If any of the maintenance actions fail.  
  
-   If **\-CkDB**, **\-CkDBNoIdx**, **\-CkAl**, **\-CkAlNoIdx**, **\-CkTxtAl**, or **\-CkCat** checks find problems with the data.  
  
-   If a general failure is encountered.  
  
## Permissions  
 The **sqlmaint** utility can be executed by any Windows user with **Read and Execute** permission on `sqlmaint.exe`, which by default is stored in the `x:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER1\MSSQL\Binn` folder. Additionally, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login specified with **\-login\_ID** must have the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] permissions required to perform the specified action. If the connection to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses Windows Authentication, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login mapped to the authenticated Windows user must have the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] permissions required to perform the specified action.  
  
 For example, using the **\-BkUpDB** requires permission to execute the BACKUP statement. And using the **\-UpdOptiStats** argument requires permission to execute the UPDATE STATISTICS statement. For more information, see the "Permissions" sections of the corresponding topics in Books Online.  
  
## Examples  
  
### A. Performing DBCC checks on a database  
  
```  
sqlmaint -S MyServer -D AdventureWorks2012 -CkDB -CkAl -CkCat -Rpt C:\MyReports\AdvWks_chk.rpt  
```  
  
### B. Updating statistics using a 15% sample in all databases in a plan. Also, shrink any of the database that have reached 110 MB to having only 10% free space  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -UpdOptiStats 15 -RmUnusedSpace 110 10  
```  
  
### C. Backing up all the databases in a plan to their individual subdirectories in the default x:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Backup directory. Also, delete any backups older than 2 weeks  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -BkUpDB -BkUpMedia DISK -UseDefDir -CrBkSubDir -DelBkUps 2weeks  
```  
  
### D. Backing up a database to the default x:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Backup directory.\\  
  
```  
sqlmaint -S MyServer -BkUpDB -BkUpMedia DISK -UseDefDir  
```  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../Topic/UPDATE%20STATISTICS%20\(Transact-SQL\).md)  
  
  