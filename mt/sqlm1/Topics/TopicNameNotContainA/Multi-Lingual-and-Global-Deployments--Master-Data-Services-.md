---
title: Multi-Lingual and Global Deployments (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
---
# Multi-Lingual and Global Deployments (Master Data Services)
  [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] supports deployment of components and tools in all languages supported by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Local Language Versions in SQL Server](../../Topics\TopicNameNotContainA/Local-Language-Versions-in-SQL-Server.md).  
  
## How languages are used  
 The following table describes the language support for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] components and tools.  
  
|Component or Tool|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Setup|Select the English Setup program when you want the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application to be available and supported in languages that differ from the Setup language. For more information, see the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] description below.|  
|[!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)]|The Setup language determines the [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] language. For example, if you choose German for the Setup language, [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] is available in German on that computer.|  
|[!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)]|When you run Setup in English, the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application is available and supported in all application languages. [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] can display in any of those application languages and accept locale\-specific input based on the language preferences of the client web browser. If the language preferences are configured for a non\-supported application language, [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] defaults to English.<br /><br /> When you run Setup in a language other than English, resources are included for the all other application languages but it is not a supported scenario for clients to use [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] in a language other than the selected Setup language. If you try to access [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] in a language different from the Setup language, you might experience problems with data display and input in the application.|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database|Information in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database is not specific to any locale. This enables [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] to determine how to display information, such as dates and numbers, in the format determined by the language preferences of the client web browser.|  
  
## See Also  
 [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md)  
  
  