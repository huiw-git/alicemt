---
title: Discontinued Management Tools Features in SQL Server 2016
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e58acd0-73c5-4161-9fbc-8ea531bc681c
---
# Discontinued Management Tools Features in SQL Server 2016
  This topic describes [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Tools features that are no longer available in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Features Removed in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 None  
  
## Features Removed in [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]  
 None  
  
## Features Removed in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]  
  
### SQL Server Compact Edition  
 The SQL Server Compact Edition code editor has been removed from [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Support for SQL Server Compact Edition has also been removed from Object Explorer, Solution Explorer, and Template Explorer. Use the Transact\-SQL editors in Microsoft Visual Studio 2010 Service Pack 1 or Webmatrix instead.  
  
### ActiveX Subsystem for SQL Server Agent  
 The ActiveX subsystem for SQL Server Agent has been removed in this release. There is no replacement functionality.  
  
### sp\_addtask, sp\_deletetask, sp\_updatetask  
 Sp\_addtask, sp\_deletetask, and sp\_updatetask have been removed in this release. Do not use this functionality in new or updated applications.  
  
### Net Send and Pager Notification  
 Net Send and Pager Notification have been removed in this release. Do not use this functionality in new or updated applications.  
  
### Data\-tier Applications  
 Some data\-tier application \(DAC\) features present in [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] have been removed in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]. However, the Data\-Tier Application Framework \(DACfx version 3.0\) released with [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] is compatible with [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] through [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] and [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)]. DAC version 3.0 is not supported by earlier versions of [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] including [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] in [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]. Visual Studio 2010 Database Projects do not support DAC 3.0 DACPAC packages or DAC Export \(BACPAC\) packages generated with DACfx version 3.0 or later.  
  
 Microsoft recommends using the latest available version [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Tools Database Projects.  
  
 DACfx 3.0 API and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools do support reading DACPAC and BACPAC files created using earlier [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools and DACfx versions: extracting databases into DACPAC files from these versions, and deploying databases into supported versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] through [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Tools.  
  
## See Also  
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)  
  
  