---
title: Download SQL Server Management Studio (SSMS)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
manager:jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Download SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) is an integrated environment for accessing, configuring, managing, administering, and developing all components of SQL Server. SSMS combines a broad group of graphical tools with a number of rich script editors to provide developers and administrators of all skill levels access to SQL Server. This release features improved compatibility with previous versions of SQL Server, a stand\-alone web installer, and toast notifications within SSMS when new releases become available.  
     
| ![download](../content/media/download.png) Download SQL Server Management Studio (SSMS)  |  
|---|  
|**[Download SQL Server Management Studio July 2016](http://go.microsoft.com/fwlink/?LinkID=820751)**|  

> [!IMPORTANT]
> This release of SSMS enables [the 'XACT_ABORT' option in SSMS](https://msdn.microsoft.com/library/ms188792.aspx#Anchor_1) by default. This option instructs SQL Server to rollback the entire transaction and abort the batch if a run-time error occurs. You can disable this option in the SQL Server Query Execution options dialog page.

> [!NOTE]  
> This generally available release of SSMS is free and does not require a SQL Server license to install and use.  

 
## SQL Server Management Studio   
**Version Information**  
  
*This release of SSMS uses the Visual Studio 2015 Isolated shell.*   
The version number for SQL Server Management Studio June 2016 generally available release is: 13.0.15500.91
  
**Supported SQL Server versions**  
  
* This version of SSMS works with all [supported versions of SQL Server (SQL Server 2008 - SQL Server 2016),](https://support.microsoft.com/en-us/lifecycle?C2=1044) and provides the greatest level of support for working with the latest cloud features in Azure SQL Database.  
* There is no explicit block for SQL Server 2000 or SQL Server 2005, but some features may not work properly.  
* Additionally, this version of SSMS can be installed side\-by\-side with earlier released non\-preview versions.  
  
**Supported Operating systems**  
  
This release of SSMS supports the following platforms when used with the latest available service pack:   
 Windows 10, Windows 8, Windows 8.1, Windows 7 (SP1), Windows Server 2012 (64\-bit), Windows Server 2012 R2 (64\-bit), Windows Server 2008 R2 (64\-bit)  
   
 **Available Languages**  
> [!NOTE]  
> Non-English localized releases of SSMS require the [KB 2862966 security update package](https://support.microsoft.com/en-us/kb/2862966) if installing on: Windows 8, Windows 7, Windows Server 2012, and Windows Server 2008 R2. 
  
 This release of SSMS can be installed in the following languages:  
[Chinese (People's Republic of China)](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x804) | [Chinese (Taiwan)](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x404) | [English (United States)](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x409) | [French](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x40c)  
[German](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x407) | [Italian](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x410) | [Japanese](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x411) | [Korean](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x412) | [Portuguese (Brazil)](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x416) | [Russian](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x419) | [Spanish](http://go.microsoft.com/fwlink/?LinkID=820751&clcid=0x40a)  

 
## Changelog  
* ***Edit, July 5th:*** Improved support for SQL Server 2016 (1200 compatibility level) tabular databases in the Analysis Services Process dialog and the Analysis Services Deployment wizard.

* ***Edit, July 5th:*** New option in SSMS 'query execution options' dialog to set 'XACT_ABORT'. This option is enabled by default in this release of SSMS and instructs SQL Server to rollback the entire transaction and abort the batch if a run-time error occurs.

* Support for Azure SQL Data Warehouse in SSMS.

* Significant updates to the SQL Server PowerShell module. This includes a new [SQL PowerShell module and new CMDLETs for Always Encrypted, SQL Agent, and SQL Error Logs](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update).

* Support for PowerShell script generation in the Always Encrypted wizard.

* Significantly improved connection times to Azure SQL databases.

* New ‘Backup to URL’ dialog to support the creation of Azure storage credentials for SQL Server 2016 database backups. This provides a more streamlined experience for storing database backups in an Azure storage account.
 
* New Restore dialog to streamline restoring a SQL Server 2016 database backup from the Microsoft Azure storage service. 

* Bug fix in SSMS query designer to allow adding tables to the designer if a user doesn’t have SELECT permissions on them.

* Bug fix to add IntelliSense support for 'TRY_CAST()', and 'TRY_CONVERT()' functions [(Microsoft Connect item #2453461)](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast).

* Bug fix in PowerShell module to enable loading of ‘SQLAS’ extension [(Microsoft Connect item #2544902)](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension).

* Bug fix in the SSMS editor window to allow drag-and-drop open of Sql files [(Microsoft Connect item #2690658)](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios).

* Bug fix in Profiler to fix Profiler crash when exiting. [(Microsoft Connect item #2616550)](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped).

* Bug fix in SSMS to prevent crash when trying to edit a join link in the SSMS table designer [(Microsoft Connect item #2721052)](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms).

* Bug fix in SSMS to enable database script generation for db_owner role members. [(Microsoft Connect item #2869241)](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june).

* Bug fix in SSMS editor to remove the delay in closing a query tab if the server has gone offline [(Microsoft Connect item #2656058)](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline).

* Bug fix to enable Backup option in SQL Server Express databases [(Microsoft Connect item #2801910)](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks).

* Bug fix in Analysis Services to correctly show the Data Feed provider for multi-dimensional Analysis Services models.

For the full list of features, see   
                [SQL Server Management Studio - Changelog &#40;SSMS&#41;](../content/SQL-Server-Management-Studio---Changelog--SSMS-.md)  
  
To see the list of known issues and work arounds, see   
                [SQL Server Management Studio -  Release Notes](../content/SQL-Server-Management-Studio----Release-Notes.md)  
  
For information about user data collection, see   
                [SQL Server Privacy Statement](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).  
  
## Previous releases  
[Previous SQL Server Management Studio Releases](../content/Previous-SQL-Server-Management-Studio-Releases.md)  
  
## Feedback  
  
![needhelp_person_icon](../content/media/needhelp_person_icon.png) [SQL Client Tools Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Log an issue or suggestion at Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## See Also  
[Tutorial: SQL Server Management Studio](assetId:///d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[SQL Server Management Studio documentation](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Additional updates and service packs](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Download SQL Server Data Tools (SSDT)](../content/Download-SQL-Server-Data-Tools--SSDT-.md)  
