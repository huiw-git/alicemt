---
title: Reporting Services Site Collection Features
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
---
# Reporting Services Site Collection Features
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode provides three SharePoint site collection features. The features support the general [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode reporting environment, [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)], a feature of the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Add\-in for [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] Enterprise Edition, and management operations for [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint Central Administration.  
  
## Site Collection Features  
 The following table describes the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] site collection features.  
  
|Feature|Description|  
|-------------|-----------------|  
|**Report Server Central Administration Feature**|Enables Features for managing integration with a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server. This feature is only installed and used in the SharePoint Central Administration site collection.<br /><br /> The Report server integration feature is automatically activated in SharePoint Central Administration Site collection after you install the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] Add\-in for SharePoint products. In some situations you will need to manually activate the feature. To activate the report server feature, use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] pages in SharePoint Central Administration's Site Settings page.<br /><br /> The [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] version and later of the Add\-in for SharePoint products will activate the report server integration feature for all existing site collections when the Add\-in is installed. Additionally, the feature will be automatically active for new site collections.|  
|**Report Server Integration Feature**|Enables rich reporting using [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]<br /><br /> This feature is Active by default.|  
|**Power View Integration Feature**|Enables interactive data exploration and visual presentation against [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] work books and Analysis services tabular databases.<br /><br /> The feature can be accessed by the context menus of the following data sources:<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> **.bism** connection file<br /><br /> <br /><br /> If [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)] does not appear in the context menus, verify the **Power View Integration Feature** is activated.<br /><br /> This feature is deactivated by default.|  
  
## See Also  
 [Activate the Report Server and Power View Integration Features in SharePoint](../../Topics\TopicNameNotContainA/Activate-the-Report-Server-and-Power-View-Integration-Features-in-SharePoint.md)   
 [Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;](../Topic/Reporting%20Services%20Site%20Settings%20and%20Site%20Features\(SharePoint%20Mode\).md)   
 [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../Topics\TopicNameNotContainA/Activate-the-Report-Server-File-Sync-Feature-in-SharePoint-Central-Administration.md)  
  
  