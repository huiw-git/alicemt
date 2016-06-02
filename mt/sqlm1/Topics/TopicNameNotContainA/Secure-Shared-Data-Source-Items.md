---
title: Secure Shared Data Source Items
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
---
# Secure Shared Data Source Items
  You can set security on a shared data source item to enable or disable access to it.  
  
 A user who has minimal access to a shared data source \(for example, the access granted through the **Browser** role\) can view the list of reports that use the item, provided the user is also authorized to view the reports themselves.  
  
 A user who has additional access \(such as that granted through the **Content Manager** role\) can view and set properties for the shared data source.  
  
 To set security, you create a role assignment that specifies which user or group account has access to the shared data source. Users who have access to a shared data source item can change its name, description, connection string, or credential information.  
  
## Tasks and Access to Items  
 When creating role assignments, use a role that has these tasks to assign appropriate permissions to users and groups.  
  
|Select this task|To give users permission to|  
|----------------------|---------------------------------|  
|View data sources|View the shared data source item in the folder hierarchy. Without this task, the item is not visible to users and they may not be aware that the data source is available.|  
|Manage data sources|View properties that specify the name, description, and connection information. This task is also used to display a shared data source item in the folder hierarchy. If you choose this task, you can omit the "View data sources" task.|  
|Set security on items|Create and modify role assignments that control access to the shared data source. This task must be used with either "View data source" or "Manage data sources" tasks. If it is not, it has no effect because the user cannot select the item.|  
  
## See Also  
 [Manage Report Data Sources](../../Topics\TopicNameNotContainA/Manage-Report-Data-Sources.md)   
 [Secure Folders](../../Topics\TopicNameNotContainA/Secure-Folders.md)   
 [Secure Reports and Resources](../../Topics\TopicNameNotContainA/Secure-Reports-and-Resources.md)   
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)   
 [Store Credentials in a Reporting Services Data Source](../../Topics\TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md)  
  
  