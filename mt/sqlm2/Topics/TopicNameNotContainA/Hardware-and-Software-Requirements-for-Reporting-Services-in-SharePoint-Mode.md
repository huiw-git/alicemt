---
title: Hardware and Software Requirements for Reporting Services in SharePoint Mode
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
---
# Hardware and Software Requirements for Reporting Services in SharePoint Mode
  This topic describes prerequisites, hardware requirements, and installation considerations for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] running in SharePoint mode. Because [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode requires a SharePoint server, most of the requirements are based on the SharePoint environment. For native mode report servers, your hardware should meet minimum hardware and software requirements for running [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
-   [Prerequisites](#bkmk_prereq)  
  
-   [Report Server Database Requirements](#bkmk_report_server_database)  
  
-   [Power View Requirements](#bkmk_powerview)  
  
-   [More Information](#bkmk_more_information)  
  
##  <a name="bkmk_prereq"></a> Prerequisites  
  
-   For local installations, the account logged in during installation of SharePoint and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] needs to be a member of the administrators group in the local operating system. The setup account does not need to be a member of the SharePoint farm administrators group.  
  
     For more information, see [Account permissions and security settings in SharePoint 2013](http://technet.microsoft.com/library/cc678863.aspx).  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] running in SharePoint mode requires SharePoint Server. For more information about SharePoint requirements and configurations, see the following:  
  
    -   [Hardware and software requirements \(SharePoint 2013\)](http://go.microsoft.com/fwlink/p/?LinkId=256365) \(http:\/\/go.microsoft.com\/fwlink\/p\/?LinkId\=256365\)  
  
    -   [Capacity management and sizing for SharePoint Server 2013](http://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Software requirements for business intelligence \(SharePoint 2013\)](http://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Hardware and software requirements \(SharePoint Server 2010\)](http://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Capacity management and sizing for SharePoint Server 2010](http://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   If you want to upgrade or update existing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint installation with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [Upgrade and Migrate Reporting Services](../../Topics\TopicNameNotContainA/Upgrade-and-Migrate-Reporting-Services.md).  
  
-   Verify the **SharePoint 2013 Administration** service is started in Windows Server Manager.  
  
###  <a name="bkmk_report_server_database"></a> Report Server Database Requirements  
  
-   Both [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] and SharePoint products and technologies use SQL Server relational databases to store application data.  
  
-   [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] requires an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] of a compatible SQL Server edition. For more information on hardware and software requirements, see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
-   SharePoint products can use an existing database instance. If an instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.  
  
-   The report server instance cannot use the SQL Server Express Edition for its database. However, the SQL Server Express Edition instance installed by the SharePoint product can exist side\-by\-side with other Database Engine editions.  
  
##  <a name="bkmk_powerview"></a> [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)] Requirements  
 Review the most up\-to\-date [Power View documentation](http://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) on Office.Microsoft.com. [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)] is a feature of Microsoft Excel 2013, and is part of the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Reporting Services add\-in for Microsoft SharePoint Server 2010 and 2013 Enterprise Editions.  
  
##  <a name="bkmk_more_information"></a> More Information  
 For information on SharePoint changes, see [Changes from SharePoint 2010 to SharePoint 2013](http://technet.microsoft.com/library/ff607742\(office.15\).aspx) \(http:\/\/technet.microsoft.com\/en\-us\/library\/ff607742\(office.15\).aspx\).  
  
 [SQL Server 2016 Release Notes](../../Topics\TopicNameNotContainA/SQL-Server-2016-Release-Notes.md)  
  
  