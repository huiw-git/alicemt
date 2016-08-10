---
title: "Upgrade SQL Server Management Tools"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Upgrade SQL Server Management Tools
[!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] supports upgrade from [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later. This topic documents support and behavior for upgrading [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Management Tools and management components such as [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent, Database Mail, Maintenance Plans, XPStar, and XPWeb.  
  
> [!IMPORTANT]  
>  For local installations, you must run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup as an administrator. If you run [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup from a remote share, you must use a domain account that has read and execute permissions on the remote share.  
  
## Known Upgrade Issues  
 Consider the following issues before you upgrade to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]:  
  
### For all upgrade scenarios:  
  
-   All TSX servers should be upgraded before the MSX server is upgraded. For more information about MSX/TSX in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Automated Administration Across an Enterprise](assetId:///44d8365b-42bd-4955-b5b2-74a8a9f4a75f).  
  
-   All components in an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] must be upgraded at the same time. Version numbers of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] components must be the same in an instance of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   You can add components to an existing installation of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] at the time that you upgrade to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. For more information, see [Upgrade to SQL Server 2016 Using the Installation Wizard (Setup)](../../Topics/TopicNameNotContainA/Upgrade-to-SQL-Server-2016-Using-the-Installation-Wizard--Setup-.md).  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Client Tools, such as [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)], the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] Tuning Advisor, sqlcmd, and osql are not upgraded to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. Instead, Client Tools run side-by-side with tools from previous [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] versions. [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] supports importing settings from earlier versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Client Tools.  
  
-   Authentication from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] will be updated from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication to Windows Authentication during upgrade. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication is not supported in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   Data for jobs and alerts will be preserved during upgrade to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   If SQLMail is being used in the instance to be upgraded, associated XPs will be supported and enabled after the upgrade. Otherwise, they will be off.  
  
-   Database Mail, also known as SQLiMail, will be upgraded with the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] component of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. By default, Database Mail will be off after upgrade. Any schema updates should be reconciled with an update script after upgrade.  
  
## See Also  
 [Supported Version and Edition Upgrades](../../Topics/TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)   
 [Backward Compatibility](assetId:///15d9117e-e2fa-4985-99ea-66a117c1e9fd)   
 [Upgrade to SQL Server 2016 Using the Installation Wizard (Setup)](../../Topics/TopicNameNotContainA/Upgrade-to-SQL-Server-2016-Using-the-Installation-Wizard--Setup-.md)