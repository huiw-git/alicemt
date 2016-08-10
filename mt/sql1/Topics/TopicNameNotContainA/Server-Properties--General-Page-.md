---
title: "Server Properties (General Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: 34
manager: mblythe
---
# Server Properties (General Page)
Use this page to view or modify the title used in Report Manager, enable or disable My Reports, select a role definition for My Reports security, and enable or disable the client print control.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], connect to a report server instance, right-click the report server name, and then select **Properties**.  
  
 The server mode determines which server properties you can set. If you are managing a report server that is configured for SharePoint integrated mode, you cannot enable My Reports or set the application title for Report Manager.  
  
## Options  
 **Name**  
 Type an application name that appears in Report Manager. By default, this value is [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]. The name that you specify appears only in Report Manager.  
  
 **Version**  
 This property is read-only. Specifies the version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] that you are using.  
  
 **Edition**  
 This property is read-only. Specifies the current report server instance. Report Manager is not available in every edition of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **Authentication Mode**  
 This property is read-only. It identifies the types of authentication requests accepted by the report server instance. To change the authentication mode, you must edit the RSReportServer.config file. For more information, see [Authentication with the Report Server](../../Topics/TopicNameNotContainA/Authentication-with-the-Report-Server.md).  
  
 **URL**  
 This property is read-only. Specifies the URL to the Report Server Web service. This value is specified in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration tool. For more information, see [Configure a URL  (SSRS Configuration Manager)](../../Topics/TopicNameContainA/Configure-a-URL---SSRS-Configuration-Manager-.md).  
  
 **Enable a My Reports folder for each user**  
 Make My Reports available to users. This option is only available for native mode report servers.  
  
 **Select the role to apply to each My Reports folder**  
 Specify a role definition to use for My Reports security. The role definition identifies the set of tasks that are supported in each My Reports folder.  
  
 **Enable download for the ActiveX client print control**  
 Sets the **EnableClientPrinting** report server system property. If you enable client printing, users who have local administrator permissions have the option of downloading a signed ActiveX control for printing HTML reports. For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../../Topics/TopicNameNotContainA/Enable-and-Disable-Client-Side-Printing-for-Reporting-Services.md).  
  
## See Also  
 [Set Report Server Properties (Management Studio)](../../Topics/TopicNameNotContainA/Set-Report-Server-Properties--Management-Studio-.md)   
 [Connect to a Report Server in Management Studio](../../Topics/TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Enable and Disable My Reports](../../Topics/TopicNameNotContainA/Enable-and-Disable-My-Reports.md)   
 [Report Server in Management Studio F1 Help](../../Topics/TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)   
 [Secure My Reports](../../Topics/TopicNameNotContainA/Secure-My-Reports.md)