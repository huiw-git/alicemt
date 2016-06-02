---
title: Configure and Administer a Report Server (SSRS Native Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
---
# Configure and Administer a Report Server (SSRS Native Mode)
  This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. It also includes a list of topics that explain how to configure specific components, features, or server capabilities. To configure [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], you can:  
  
-   Use the Reporting Services Configuration Manager. Many of the topics in this section contain information about how to configure specific features through this tool.  
  
-   Use [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] to customize server properties, enable My Reports, enable trace logs, and set site\-wide defaults. For more information about site settings, see [Reporting Services Report Server &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(Native%20Mode\).md) for Management Studio. Note that you can create and run script that sets server properties programmatically. For more information, see [Script Deployment and Administrative Tasks](../../Topics\TopicNameNotContainA/Script-Deployment-and-Administrative-Tasks.md) and [Report Server System Properties](../Topic/Report%20Server%20System%20Properties.md).  
  
-   Use Report Manager to grant permissions to access the report server. Permissions are conveyed through role assignments that you define for each user or group account. For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../Topic/Roles%20and%20Permissions%20\(Reporting%20Services\).md).  
  
-   Optionally, modify configuration files to change application settings. For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md).  
  
## In This Section  
 [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20Report%20Server%20URLs%20%20\(SSRS%20Configuration%20Manager\).md)  
 Describes how to define the URLs used to access the report server and Report Manager.  
  
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Report%20Server%20Service%20Account%20\(SSRS%20Configuration%20Manager\).md)  
 Provides recommendations and steps on how to modify service account and password.  
  
 [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)  
 Describes how to create a report server database, required for storing server metadata and objects.  
  
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)  
 Describes how to modify the connection string used by the report server to connect to the report server database.  
  
 [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83)  
 Describes how to configure a report server to support e\-mail report distribution.  
  
 [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Unattended%20Execution%20Account%20\(SSRS%20Configuration%20Manager\).md)  
 Describes how to configure a user account to process reports in unattended mode.  
  
## See Also  
 [Configure Report Builder Access](../../Topics\TopicNameNotContainA/Configure-Report-Builder-Access.md)   
 [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md)   
 [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md)   
 [Reporting Services Security and Protection](../../Topics\TopicNameNotContainA/Reporting-Services-Security-and-Protection.md)   
 [Reporting Services Report Server &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(Native%20Mode\).md)  
  
  