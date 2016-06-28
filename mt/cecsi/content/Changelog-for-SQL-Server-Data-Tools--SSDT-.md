---
title: Changelog for SQL Server Data Tools (SSDT)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
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
# Changelog for SQL Server Data Tools (SSDT)
This change log is for [SQL Server Data Tools (SSDT) Preview for Visual Studio 2015](https://msdn.microsoft.com/library/mt204009.aspx), co\-released with SQL Server 2016 Preview.  
  
## SSDT April (for SQL Server 2016 RC3)  
Released: April 15, 2016  
  
Build number: 14.0.60413.0  
  
**SQL Server Database**  
* **Always Encrypted Support:** For Databases that contain Always Encrypted columns, SSDT and DacFx allows viewing and editing these databases and publishing from a database project to them. Note that support for altering columns with column encryption present will be coming in a future release.  
* **Connection dialog and SQL Server Object Explorer:** Multiple fixes and improvements.  
    * The Details page listing advanced connection properties was overhauled to show the full connection string in a multi-line box, and to improve support on High DPI machines.  
    * We have brought back the traditional error dialog with detailed connection errors. This helps when diagnosing login issues with clearer error messages and a stack trace so that DBAs or CSS can get the information they need to help diagnose your problems.  
    * For users with minimal permissions we fixed a number of issues around listing databases in the Connection Dialog and SQL Server Object Explorer, viewing the Security folder, and more.  
    * Azure SQL DB performance when expanding the databases node to list all DBs has been improved.  
* **SSDT installer:**  
    * Fixed issue where .Net was being downloaded on uninstall.  
    * The installer size is now set correctly on High DPI machines.  
    * Removed the version check blocking SSDT installation if a newer SQL Server version is present.  
    * Schema Compare: Fixed a performance issue where checking/unchecking multiple items took a long time in Visual Studio.  
    * Support for using LocalDB 2014 on x86 machines, since there is no x86 version of SQL Server 2016.  
* **Build and Deployment:**  
    * Fixed issue where computed columns were not supported on Temporal Tables.  
    * The “Execute deployment script in single-user mode” option is ignored when deploying to Azure V12 as this is not supported in cloud scenarios.  
  
  
## SSDT Hotfix (for SQL Server 2016 RC2)  
Released: April 5, 2016  
  
Build number: 14.0.60329.0  
  
This build contains a hotfix for the version of SSDT that provides features for SQL Server Integration Services. Build 14.0.60316.0 can also be used with Analysis Services and Reporting Services in SQL Server 2016.   
  
To get this hotfix, use the [download links on this blog post](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/).  
  
Report developers, if you build new reports using this build of SSDT, [read the known issue and workaround](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/) for a  for a temporary issue in SSRS reports found only in this hotfix.  
  
## SSDT Hotfix (for SQL Server 2016 RC0)  
Released: March 18, 2016  
  
Build number: 14.0.60316.0  
  
This build contains a hotfix for the version of SSDT that provides features for SQL Server 2016 RC0. There is no RC1 version of SSDT at this time. Build 14.0.60316.0 can be used with either RC0 or RC1 of SQL Server 2016.  
      
## SSDT February 2016 Preview (for SQL Server 2016 RC0)  
Released: March 7, 2016  
  
Build number: 14.0.60305.0  
  
-   **SQL Server project templates**  
  
    No announcements for this SSDT preview release. See [What's New in Database Engine](https://msdn.microsoft.com/library/bb510411.aspx) to learn about other features in this release.  
  
-   **SSIS package project templates**  
  
    SSIS Designer creates and maintains packages for SQL Server 2016, 2014, or 2012. New templates renamed as parts. SSIS Hadoop connector supports for ORC format. See [What's New in Integration Services](https://msdn.microsoft.com/library/bb522534.aspx) for details.  
  
-   **SSAS project templates (Tabular model projects)**  
  
    This month’s update to Analysis Services delivers support for display folders for Tabular models and any models created with new SQL Server 2016 compatibility level is now supported in SSIS packages. For more information. see [What's New in Analysis Services (blog post)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx) for details.  
  
-   **SSRS report project templates**  
  
    No announcements for this SSDT preview release. See [What's New in Reporting Services](https://msdn.microsoft.com/library/ms170438.aspx) to learn  about other features in this release.  
  
## SSDT January 2016 Preview  
Released: Feb 4, 2016  
  
Build number: 14.0.60203.0  
  
-   **SQL Server project templates**  
  
    No announcements for this SSDT preview release. See [What's New in Database Engine](https://msdn.microsoft.com/library/bb510411.aspx) to learn about other features in this CTP.  
  
-   **SSIS package project templates**  
  
    Adds support for ODBC source and destination components, a CDC control task,  
      a CDC source and splitter component, a Microsoft Connector for SAP BW, and an Integration Services Feature Pack for Azure. See [What's New in Integration Services](https://msdn.microsoft.com/library/bb522534.aspx) for details.  
  
-   **SSAS project templates**  
  
    Includes enhancements for Tabular models at 1200 compatibility level, calculated columns and row\-level security for models in DirectQuery mode, translations of model metadata,  TMSL script execution in the SSIS Analysis Services Execute DDL Task, and numerous bug fixes.  
    See [What's New in Analysis Services (msdn)](https://msdn.microsoft.com/library/bb522628.aspx) or [What's New in Analysis Services (blog post)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx) for details.  
  
-   **SSRS report project templates**  
  
    No announcements for this SSDT preview release. See [What's New in Reporting Services](https://msdn.microsoft.com/library/ms170438.aspx) to learn  about other features in this CTP.  
  
## SSDT December 2015 Preview  
  
-   **SQL Server project templates** include bug fixes for the Connection dialog box, recent history lists, proper use of authentication context set in the connection property when loading a database list.  
  
    -   Changed test connection timeout value to 15 seconds.  
  
    -   Create an Azure SQL Database server firewall rule if the client IP is not registered when loading a database list.  
  
    -   SQL Server 2016 CTP3.2 feature programmability support.  
  
-   **SSAS project templates** add support for creating calculated tables based on DAX expressions and other objects already defined in the model.  
  
-   **SSIS package project template** additions include SSIS Hadoop connector support for Avro file format and Kerberos authentication.   
    Please note that SSIS designer support for SSIS 2012 and 2014 is not yet included in this update.  
  
## SSDT November 2015 Preview  
  
-   **SQL Server project templates**. Preview of improved connection experience for SQL Server and Azure SQL Database.  
  
-   **SSIS package project templates**. SSIS catalog performance improvement: The performance for most SSIS catalog views for non\-ssis\-admin user is improved.  
  
-   **SSAS project templates** include enhancements for Tabular model projects in Analysis Services. You can use the **View Code** command to view the model definition in JSON. If you aren't using a full\-featured edition Visual Studio 2015, you will need one to get the JSON editor. You can download the [Visual Studio Community edition](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) for free.  
  
## SSDT October 2015 Preview  
  
-   New project  templates for BI (Analysis Services models, Reporting Services reports, and Integration Services packages). All  SQL Server project templates are now in one SSDT.  
  
-   New SSIS features including Hadoop connector, control flow template, relaxed max buffer size of data flow task.  
  
-   SQL Server 2016 CTP 3.0 feature support for relational database projects.  
  
-   Various bug fixes in SSIS and support for Windows 7 OS.  
  
## SSDT September 2015 Preview  
  
-   Multi\-language support is new in this preview.  
  
## SSDT August 2015 Preview  
  
-   New standalone Setup.exe program for installing SSDT.  You no longer need to use a modified version of SQL Server Setup. This version of SSDT includes a project template for building relational databases deployed to SQL Server or Azure SQL Database.  
  
## See Also  
[Download SQL Server Data Tools &#40;SSDT&#41;](../content/Download-SQL-Server-Data-Tools--SSDT-.md)  
[Previous releases of SQL Server Data Tools &#40;SSDT and SSDT-BI&#41;](../content/Previous-releases-of-SQL-Server-Data-Tools--SSDT-and-SSDT-BI-.md)  
[What's New in Database Engine](https://msdn.microsoft.com/library/bb510411.aspx)  
[What's New in Analysis Services](https://msdn.microsoft.com/library/bb522628.aspx)  
[What's New in Integration Services](https://msdn.microsoft.com/library/bb522534.aspx)  
  
