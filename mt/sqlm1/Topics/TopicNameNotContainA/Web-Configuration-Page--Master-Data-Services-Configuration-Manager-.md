---
title: Web Configuration Page (Master Data Services Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
---
# Web Configuration Page (Master Data Services Configuration Manager)
  Use the **Web Configuration** page to configure a website and web application. You can also enable Data Quality Services.  
  
## Configure the Web Application  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Website**|Either create a new website, select the default website, or select another available site \(if listed\). This list displays the websites that are defined in Internet Information Services \(IIS\) on the local computer. When you create a new website, a new web application is automatically created. When you select the default or another existing site, you must create an application manually.|  
|**Web application**|Select a [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application for configuration. This box shows the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web applications in the selected website only.<br /><br /> If nothing is displayed, click **Create** to create a website.|  
|**Create**|Opens the **Create Web Application** dialog box from which you create a [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application in the selected site. This button is enabled only when the selected site has no root web application configured as the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.|  
  
## Associate Application with Database  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Select**|Opens the **Connect to Server** dialog box from which you connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance and select a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database to associate with the selected [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.|  
|**SQL Server instance**|Displays the name of the selected [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that hosts the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. This is blank until you connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance and select a database.|  
|**Database**|Displays the name of the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database that is associated with the selected [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application. This is blank until you connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance and select a database.|  
  
## Enable DQS Integration  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Enable integration with Data Quality Services**|Select this option to enable the Data Quality functionality available in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)]. For more information, see [Enable Data Quality Services Integration with Master Data Services](../../Topics\TopicNameNotContainA/Enable-Data-Quality-Services-Integration-with-Master-Data-Services.md).|  
  
## See Also  
 [Get Started with Master Data Services &#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md)   
 [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](../Topic/Create%20a%20Master%20Data%20Manager%20Web%20Application%20\(Master%20Data%20Services\).md)  
  
  