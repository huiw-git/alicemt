---
title: "Configure and Administer a Report Server (SSRS Native Mode)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 52
caps.handback.revision: 0
manager: mblythe
---
# Configure and Administer a Report Server (SSRS Native Mode)
This topic summarizes the approaches that you can use to configure [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]. It also includes a list of topics that explain how to configure specific components, features, or server capabilities. To configure [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)], you can:  
  
-   Use the Reporting Services Configuration Manager. Many of the topics in this section contain information about how to configure specific features through this tool.  
  
-   Use [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] to customize server properties, enable My Reports, enable trace logs, and set site-wide defaults. For more information about site settings, see [Reporting Services Report Server (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Report-Server--Native-Mode-.md) for Management Studio. Note that you can create and run script that sets server properties programmatically. For more information, see [Script Deployment and Administrative Tasks](../../Topics/TopicNameNotContainA/Script-Deployment-and-Administrative-Tasks.md) and [Report Server System Properties](assetId:///cd874117-00e5-4ae6-8629-eb9ba9f40478).  
  
-   Use Report Manager to grant permissions to access the report server. Permissions are conveyed through role assignments that you define for each user or group account. For more information, see [Roles and Permissions (Reporting Services)](../../Topics/TopicNameNotContainA/Roles-and-Permissions--Reporting-Services-.md).  
  
-   Optionally, modify configuration files to change application settings. For more information about each file and guidelines for modifying them, see [Reporting Services Configuration Files](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Files.md).  
  
## In This Section  
 [Configure Report Server URLs  (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Report-Server-URLs---SSRS-Configuration-Manager-.md)  
 Describes how to define the URLs used to access the report server and Report Manager.  
  
 [Configure the Report Server Service Account (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-the-Report-Server-Service-Account--SSRS-Configuration-Manager-.md)  
 Provides recommendations and steps on how to modify service account and password.  
  
 [Create a Report Server Database  (SSRS Configuration Manager)](../../Topics/TopicNameContainA/Create-a-Report-Server-Database---SSRS-Configuration-Manager-.md)  
 Describes how to create a report server database, required for storing server metadata and objects.  
  
 [Configure a Report Server Database Connection  (SSRS Configuration Manager)](../../Topics/TopicNameContainA/Configure-a-Report-Server-Database-Connection---SSRS-Configuration-Manager-.md)  
 Describes how to modify the connection string used by the report server to connect to the report server database.  
  
 [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83)  
 Describes how to configure a report server to support e-mail report distribution.  
  
 [Configure the Unattended Execution Account (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-the-Unattended-Execution-Account--SSRS-Configuration-Manager-.md)  
 Describes how to configure a user account to process reports in unattended mode.  
  
## See Also  
 [Configure Report Builder Access](../../Topics/TopicNameNotContainA/Configure-Report-Builder-Access.md)   
 [Reporting Services Configuration Files](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Files.md)   
 [Reporting Services Configuration Manager (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager--Native-Mode-.md)   
 [Reporting Services Security and Protection](../../Topics/TopicNameNotContainA/Reporting-Services-Security-and-Protection.md)   
 [Reporting Services Report Server (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Report-Server--Native-Mode-.md)