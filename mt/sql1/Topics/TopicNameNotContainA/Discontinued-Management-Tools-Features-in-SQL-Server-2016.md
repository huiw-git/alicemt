---
title: "Discontinued Management Tools Features in SQL Server 2016"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e58acd0-73c5-4161-9fbc-8ea531bc681c
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Discontinued Management Tools Features in SQL Server 2016
This topic describes [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Management Tools features that are no longer available in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
## Features Removed in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]  
 None  
  
## Features Removed in [!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]  
 None  
  
## Features Removed in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]  
  
### SQL Server Compact Edition  
 The SQL Server Compact Edition code editor has been removed from [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. Support for SQL Server Compact Edition has also been removed from Object Explorer, Solution Explorer, and Template Explorer. Use the Transact-SQL editors in Microsoft Visual Studio 2010 Service Pack 1 or Webmatrix instead.  
  
### ActiveX Subsystem for SQL Server Agent  
 The ActiveX subsystem for SQL Server Agent has been removed in this release. There is no replacement functionality.  
  
### sp_addtask, sp_deletetask, sp_updatetask  
 Sp_addtask, sp_deletetask, and sp_updatetask have been removed in this release. Do not use this functionality in new or updated applications.  
  
### Net Send and Pager Notification  
 Net Send and Pager Notification have been removed in this release. Do not use this functionality in new or updated applications.  
  
### Data-tier Applications  
 Some data-tier application (DAC) features present in [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] have been removed in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]. However, the Data-Tier Application Framework (DACfx version 3.0) released with [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] is compatible with [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] through [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] and [!INCLUDE[ssSDSfull](../../Topics/TopicNameContainA/tokens/ssSDSfull_md.md)]. DAC version 3.0 is not supported by earlier versions of [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] including [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] in [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)]. Visual Studio 2010 Database Projects do not support DAC 3.0 DACPAC packages or DAC Export (BACPAC) packages generated with DACfx version 3.0 or later.  
  
 Microsoft recommends using the latest available version [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Data Tools Database Projects.  
  
 DACfx 3.0 API and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] tools do support reading DACPAC and BACPAC files created using earlier [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] tools and DACfx versions: extracting databases into DACPAC files from these versions, and deploying databases into supported versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] through [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] or [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Data Tools.  
  
## See Also  
 [Backward Compatibility](assetId:///15d9117e-e2fa-4985-99ea-66a117c1e9fd)