---
title: Change Data Capture Service for Oracle by Attunity
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
---
# Change Data Capture Service for Oracle by Attunity
  The CDC Service for Oracle is a Windows service that scans Oracle transaction logs and captures changes to Oracle tables of interest into [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] change tables. The SQL change tables where the changes captured from Oracle are stored are the same type of change tables used in the native [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Change Data Capture feature. This makes consuming these changes as easy as consuming changes made to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases.  
  
## Installation  
 The Microsoft® Change Data Capture Designer and Service for Oracle by Attunity for Microsoft SQL Server® 2016 are part of the SQL Server 2016 Feature Pack. Download components of the Feature Pack from the [SQL Server 2016 Feature Pack web page](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
 The CDC Service for Oracle can be installed on any supported Windows computer with access to the source Oracle database\(s\) being captured and the target [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance where the target CDC database resides. The CDC Service does not need a local installation of the Oracle database or the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, only their supported clients. For information about where to install the required database components, see **Database Prerequisites** in this topic.  
  
 The installation of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] CDC Service for Oracle places the service configuration UI and the service program in the selected location. The CDC Service for Oracle is configured separately using the Oracle CDC Service Configuration Console. For more information on configuring the Oracle CDC Service, see [Change Data Capture Service for Oracle by Attunity F1 Help](../../Topics\TopicNameNotContainA/Change-Data-Capture-Service-for-Oracle-by-Attunity-F1-Help.md).  
  
 The CDC Service for Oracle can be installed on any supported Windows computer where the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Native Client is installed; it does not need to be installed on the same computer where the target [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed.  
  
## Supported Windows Environments  
 The Change Data Capture Service for Oracle by Attunity can run in the following Windows environments:  
  
-   Windows 8  
  
-   Windows 7  
  
-   Windows Server 2012  
  
-   Windows Server 2008 R2 with Service Pack 1  
  
-   Windows Server 2008 with Service Pack 2  
  
## Database Prerequisites  
 To work with the CDC Service for Oracle you must install the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Native Client Oracle software. This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service. Additionally, you need to install the SQL Server ODBC Client using SQL Server Setup.  
  
 The CDC Service for Oracle supports the following versions:  
  
### Source Oracle Database  
  
-   Oracle Database 11x, any version  
  
-   Oracle Database 10x, any version  
  
-   Oracle Database 10g Release 2: 10.2.0.1\-10.2.0.5 \(patchset as of April 2010\)  
  
-   Oracle Database 11g Release 1: 11.1.0.6\-11.1.0.7 \(patchset as of September 2008\)  
  
-   Oracle Database 11g Release 2: 11.2.0.1\-11.2.0.3 \(patchset as of September 2011\)  
  
### Target SQL Server Database  
 For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## Running the Installation Program  
 To install the CDC Service for Oracle, open the installation wizard for the Windows platform you are using \(32\/64\-bit\) and follow the directions on the screen.  
  
## Uninstalling Change Data Capture Service for Oracle by Attunity  
 You uninstall the CDC Service for Oracle using Control Panel, Programs and Features.  
  
 Uninstalling the CDC Service does not delete the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases created. For complete removal of the tool, you must remove the MSXDBCDC database and the specific CDC databases that were created in the target [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance you worked with.  
  
 If you uninstall the CDC Service software from one machine and install it on another computer, you only need to provide the following definitions:  
  
-   Service account  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connect string and credentials  
  
-   The master password  
  
 All the other definitions are stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and are available from the previous installation on another computer.  
  
## In This Documentation  
  
-   [Change Data Capture Service for Oracle by Attunity System Architecture](../../Topics\TopicNameNotContainA/Change-Data-Capture-Service-for-Oracle-by-Attunity-System-Architecture.md)  
  
-   [The Oracle CDC Service](../../Topics\TopicNameNotContainA/The-Oracle-CDC-Service.md)  
  
-   [Change Data Capture Service for Oracle by Attunity F1 Help](../../Topics\TopicNameNotContainA/Change-Data-Capture-Service-for-Oracle-by-Attunity-F1-Help.md)  
  
-   [Change Data Capture Service for Oracle by Attunity How to Guide](../../Topics\TopicNameNotContainA/Change-Data-Capture-Service-for-Oracle-by-Attunity-How-to-Guide.md)  
  
## See Also  
 [Working with the Oracle CDC Service](../../Topics\TopicNameNotContainA/Working-with-the-Oracle-CDC-Service.md)  
  
  