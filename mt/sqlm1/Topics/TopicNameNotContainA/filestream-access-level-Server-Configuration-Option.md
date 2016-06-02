---
title: filestream access level Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
---
# filestream access level Server Configuration Option
  Use the filestream\_access\_level option to change the FILESTREAM access level for this instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  Before this option has any effect, the Windows administration settings for FILESTREAM must be enabled. You can enable these settings when you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
|Value|Definition|  
|-----------|----------------|  
|0|Disables FILESTREAM support for this instance.|  
|1|Enables FILESTREAM for [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access.|  
|2|Enables FILESTREAM for [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] and Win32 streaming access.|  
  
## See Also  
 [Database Engine Configuration - Filestream](../../Topics\TopicNameNotContainA/Database-Engine-Configuration---Filestream.md)   
 [Enable and Configure FILESTREAM](../../Topics\TopicNameNotContainA/Enable-and-Configure-FILESTREAM.md)  
  
  