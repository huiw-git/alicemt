---
title: Upgrade SQL Server Management Tools
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
---
# Upgrade SQL Server Management Tools
  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] supports upgrade from [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] and later. This topic documents support and behavior for upgrading [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Tools and management components such as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, Database Mail, Maintenance Plans, XPStar, and XPWeb.  
  
> [!IMPORTANT]  
>  For local installations, you must run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup as an administrator. If you run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup from a remote share, you must use a domain account that has read and execute permissions on the remote share.  
  
## Known Upgrade Issues  
 Consider the following issues before you upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]:  
  
### For all upgrade scenarios:  
  
-   All TSX servers should be upgraded before the MSX server is upgraded. For more information about MSX\/TSX in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Automated Administration Across an Enterprise](../Topic/Automated%20Administration%20Across%20an%20Enterprise.md).  
  
-   All components in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be upgraded at the same time. Version numbers of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components must be the same in an instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   You can add components to an existing installation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] at the time that you upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md).  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Client Tools, such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)], the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] Tuning Advisor, sqlcmd, and osql are not upgraded to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. Instead, Client Tools run side\-by\-side with tools from previous [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions. [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] supports importing settings from earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Client Tools.  
  
-   Authentication from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will be updated from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication to Windows Authentication during upgrade. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication is not supported in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   Data for jobs and alerts will be preserved during upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   If SQLMail is being used in the instance to be upgraded, associated XPs will be supported and enabled after the upgrade. Otherwise, they will be off.  
  
-   Database Mail, also known as SQLiMail, will be upgraded with the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] component of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. By default, Database Mail will be off after upgrade. Any schema updates should be reconciled with an update script after upgrade.  
  
## See Also  
 [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)   
 [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)  
  
  