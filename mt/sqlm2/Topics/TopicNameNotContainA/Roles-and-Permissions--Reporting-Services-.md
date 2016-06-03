---
title: Roles and Permissions (Reporting Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
---
# Roles and Permissions (Reporting Services)
  Reporting Services provides an authentication subsystem and role\-based authorization model. Authentication and authorization models vary depending on whether the report server runs in native mode or SharePoint mode. If the report server is part of a SharePoint deployment, SharePoint permissions determine who has access to the report server.  
  
## Identity and Access Control for Native Mode  
 Default authentication is based on Windows Authentication and integrated security. You can change the authentication settings to allow the report server to respond to different authentication requests, or even replace the default security features with a custom authentication extension that you provide.  
  
 Authorization is based on roles that you assign to a principle. Each role consists of a set of related tasks, which are in turn composed of related operations. For example, the **Manage reports** task grants access to the following report server operations: view reports, add report, update report, delete report, schedule report, and update report properties.  
  
## Identity and Access Control for SharePoint Mode  
 In SharePoint integrated mode, authentication and authorization are handled on the SharePoint site, before requests reach the report server. Depending on how you configure authentication, requests from a SharePoint site include a security token or a trusted user name. Permissions that you set for SharePoint users and groups authorize access to report server items that are placed in SharePoint libraries.  
  
## In This Section  
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)  
 Describes the role\-based authorization model that provides access to content and operations.  
  
 [Granting Permissions on Report Server Items on a SharePoint Site](../../Topics\TopicNameContainA/Granting-Permissions-on-Report-Server-Items-on-a-SharePoint-Site.md)  
 Explains how SharePoint groups, permission levels, and permissions are used to control access to a report server.  
  
## See Also  
 [Authentication with the Report Server](../../Topics\TopicNameNotContainA/Authentication-with-the-Report-Server.md)   
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)  
  
  