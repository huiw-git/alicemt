---
title: Install Reporting Services SharePoint Mode
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
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint, enables report creation and viewing in document libraries, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription delivery of reports through email,  [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)], data alerting, and report management features, all in a deployment of based of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] SharePoint. For more information regarding features in SharePoint mode, see the section “Feature Support and Behavior Differences by Server Mode” in [Reporting Services Report Server](../../Topics\TopicNameNotContainA/Reporting-Services-Report-Server.md)  
  
 There are two core [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components to install for [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint mode:  
  
|Installation|Description|  
|------------------|-----------------|  
|**Report Sever:** The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server installed in SharePoint Mode|The report server handles the data and report processing and rendering as well subscription and Data Alert processing. The SharePoint mode report server is designed and installed as a SharePoint Shared Service.<br /><br /> **How:** Use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation media to install the report server.|  
|**Add\-in:** The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint products, **rssharepoint.msi**.|The add\-in installs the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] user interface \(UI\) pages and features on a SharePoint web front\-end server. The UI features include [!INCLUDE[ssCrescent](../../Token\Other/ssCrescent_md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Data Alerting pages.<br /><br /> **How:**  The add\-in can be installed from either a Web download or the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation media. For more information,  see [Where to find the Reporting Services add-in for SharePoint Products](../../Topics\TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md).|  
  
## In This Section  
 [Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2016&#41;](../Topic/Supported%20Combinations%20of%20SharePoint%20and%20Reporting%20Services%20Server%20and%20Add-in%20\(SQL%20Server%202016\).md)  
  
 [Where to find the Reporting Services add-in for SharePoint Products](../../Topics\TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md)  
  
 [Install The First Report Server in SharePoint Mode](../../Topics\TopicNameNotContainA/Install-The-First-Report-Server-in-SharePoint-Mode.md)  
  
 [Install or Uninstall the Reporting Services Add-in for SharePoint](../../Topics\TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md)  
  
 [Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;](../Topic/Add%20an%20Additional%20Report%20Server%20to%20a%20Farm%20\(SSRS%20Scale-out\).md)  
  
 [Add an Additional Reporting Services Web Front-end to a Farm](../../Topics\TopicNameContainA/Add-an-Additional-Reporting-Services-Web-Front-end-to-a-Farm.md)  
  
 [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../Topic/Configure%20E-mail%20for%20a%20Reporting%20Services%20Service%20Application%20\(SharePoint%202010%20and%20SharePoint%202013\).md)  
  
 [Provision Subscriptions and Alerts for SSRS Service Applications](../../Topics\TopicNameNotContainA/Provision-Subscriptions-and-Alerts-for-SSRS-Service-Applications.md)  
  
 [Claims to Windows Token Service &#40;c2WTS&#41; and Reporting Services](../Topic/Claims%20to%20Windows%20Token%20Service%20\(c2WTS\)%20and%20Reporting%20Services.md)  
  
## See Also  
 [Data Alerts Architecture and Workflow](../../Topics\TopicNameNotContainA/Reporting-Services-Data-Alerts.md)   
 [Data Alert Manager for Alerting Administrators](../../Topics\TopicNameNotContainA/Data-Alert-Manager-for-Alerting-Administrators.md)  
  
  