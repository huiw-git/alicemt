---
title: Install Reporting Services SharePoint Mode
H1: na
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
---
# Install Reporting Services SharePoint Mode
  [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] in SharePoint, enables report creation and viewing in document libraries, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] subscription delivery of reports through email,  [!INCLUDE[ssCrescent](../../Topics/TopicNameContainA/includes/ssCrescent_md.md)], data alerting, and report management features, all in a deployment of based of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] SharePoint. For more information regarding features in SharePoint mode, see the section “Feature Support and Behavior Differences by Server Mode” in [Reporting Services Report Server](../../Topics/TopicNameNotContainA/Reporting-Services-Report-Server.md)  
  
 There are two core [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] components to install for [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] in SharePoint mode:  
  
|Installation|Description|  
|------------------|-----------------|  
|**Report Sever:** The [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] report server installed in SharePoint Mode|The report server handles the data and report processing and rendering as well subscription and Data Alert processing. The SharePoint mode report server is designed and installed as a SharePoint Shared Service.<br /><br /> **How:** Use the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] installation media to install the report server.|  
|**Add-in:** The [!INCLUDE[msCoName](../../Topics/TopicNameContainA/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] add-in for SharePoint products, **rssharepoint.msi**.|The add-in installs the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] user interface (UI) pages and features on a SharePoint web front-end server. The UI features include [!INCLUDE[ssCrescent](../../Topics/TopicNameContainA/includes/ssCrescent_md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Data Alerting pages.<br /><br /> **How:**  The add-in can be installed from either a Web download or the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] installation media. For more information,  see [Where to find the Reporting Services add-in for SharePoint Products](../../Topics/TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md).|  
  
## In This Section  
 [Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2016&#41;](../../Topics/TopicNameNotContainA/Supported-Combinations-of-SharePoint-and-Reporting-Services-Server-and-Add-in--SQL-Server-2016-.md)  
  
 [Where to find the Reporting Services add-in for SharePoint Products](../../Topics/TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md)  
  
 [Install The First Report Server in SharePoint Mode](../../Topics/TopicNameNotContainA/Install-The-First-Report-Server-in-SharePoint-Mode.md)  
  
 [Install or Uninstall the Reporting Services Add-in for SharePoint](../../Topics/TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md)  
  
 [Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;](../../Topics/TopicNameContainA/Add-an-Additional-Report-Server-to-a-Farm--SSRS-Scale-out-.md)  
  
 [Add an Additional Reporting Services Web Front-end to a Farm](../../Topics/TopicNameContainA/Add-an-Additional-Reporting-Services-Web-Front-end-to-a-Farm.md)  
  
 [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2013 and SharePoint 2016&#41;](assetId:///38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [Provision Subscriptions and Alerts for SSRS Service Applications](../../Topics/TopicNameNotContainA/Provision-Subscriptions-and-Alerts-for-SSRS-Service-Applications.md)  
  
 [Claims to Windows Token Service &#40;c2WTS&#41; and Reporting Services](../../Topics/TopicNameNotContainA/Claims-to-Windows-Token-Service--c2WTS--and-Reporting-Services.md)  
  
## See Also  
 [Data Alerts Architecture and Workflow](../../Topics/TopicNameNotContainA/Reporting-Services-Data-Alerts.md#AlertingWF)   
 [Data Alert Manager for Alerting Administrators](../../Topics/TopicNameNotContainA/Data-Alert-Manager-for-Alerting-Administrators.md)  
  
  