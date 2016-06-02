---
title: System-Level Tasks
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
---
# System-Level Tasks
  A system\-level task is a collection of permissions that relate to operations that apply to the report server site as a whole. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] also includes item\-level tasks that apply to specific items. For more information, see [Item-Level Tasks](../../Topics\TopicNameNotContainA/Item-Level-Tasks.md). For more information about tasks and permissions in general, see [Tasks and Permissions](../../Topics\TopicNameNotContainA/Tasks-and-Permissions.md).  
  
> [!NOTE]  
>  If you are working with these tasks programmatically, you must use methods that support system\-level tasks. For more information, see [ListTasks](assetId:///M:ReportService2010.ReportingService2010.ListTasks(System.String)) and [ListRoles](assetId:///M:ReportService2010.ReportingService2010.ListRoles(System.String,System.String)).  
  
## Permissions in System\-Level Tasks  
 The following table identifies the collection of permissions for each system task. Permissions are listed for informational purposes only, to provide a more exact description of the functionality available through each task.  
  
|Task|Permissions|  
|----------|-----------------|  
|Execute report definitions|Execute Report Definitions \(the permission and task name are the same\)|  
|Generate events|Generate Events|  
|Manage jobs|Read System Properties<br /><br /> Update System Properties|  
|Manage report server properties|Read System Properties<br /><br /> Update System Properties|  
|Manage roles|Create Roles<br /><br /> Delete Roles<br /><br /> Read Role Properties<br /><br /> Update Role Properties|  
|Manage shared schedules|Create Schedules|  
|Manage report server security|Read System Security Policies<br /><br /> Update System Security Policies|  
|View report server properties|Read System Properties|  
|View shared schedules|Read Schedules|  
  
## See Also  
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)  
  
  