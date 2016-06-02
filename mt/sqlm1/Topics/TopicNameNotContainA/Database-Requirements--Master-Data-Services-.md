---
title: Database Requirements (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
---
# Database Requirements (Master Data Services)
  All master data is stored in a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
 Use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database on either a local or a remote computer. If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web service and [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] to the database in its new location.  
  
> [!NOTE]  
>  Any computer on which you install components of [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] must be licensed. For more information, refer to the End User License Agreement \(EULA\).  
  
## Requirements  
 Before you create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, ensure the following requirements are met.  
  
### SQL Server Edition  
 The [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
-   [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Business Intelligence \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Enterprise \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Developer \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Business Intelligence \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Enterprise \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Developer \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] Business Intelligence \(64\-bit\) x64  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] Enterprise \(64\-bit\) x64 – Upgrade from [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] Enterprise only  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] Developer \(64\-bit\) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise \(64\-bit\) x64  
  
-   Microsoft SQL Server 2008 R2 Developer \(64\-bit\) x64  
  
 For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
### Operating System  
 For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
### Accounts and Permissions  
  
|Type|Description|  
|----------|-----------------|  
|User account|In [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account to connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to host the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. For more information about the **sysadmin** role, see [Server-Level Roles](../../Topics\TopicNameNotContainA/Server-Level-Roles.md).|  
|[!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] administrator account|When you create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] system administrator. For all [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web applications associated with this database, this user can update all models and all data in all functional areas. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).|  
  
### Database Backup  
 As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment. For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md).  
  
## See Also  
 [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md)   
 [Create a Master Data Services Database](../../Topics\TopicNameContainA/Create-a-Master-Data-Services-Database.md)   
 [Master Data Services Database](../../Topics\TopicNameNotContainA/Master-Data-Services-Database.md)   
 [Connect to a Master Data Services Database Dialog Box](../../Topics\TopicNameContainA/Connect-to-a-Master-Data-Services-Database-Dialog-Box.md)   
 [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../Topic/Create%20Database%20Wizard%20\(Master%20Data%20Services%20Configuration%20Manager\).md)  
  
  