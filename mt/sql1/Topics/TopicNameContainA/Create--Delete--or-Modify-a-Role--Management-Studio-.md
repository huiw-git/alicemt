---
title: "Create, Delete, or Modify a Role (Management Studio)"
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
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
caps.latest.revision: 43
caps.handback.revision: 0
manager: mblythe
---
# Create, Delete, or Modify a Role (Management Studio)
Reporting Services provides predefined roles that define a level of access to a report server. Each user or group who requires access to report server does so through a role that describes the tasks that can be performed. Roles are defined for the report server as a whole. You cannot vary a role definition for specific parts of the report server, or specify that a role be used differently depending on the circumstances.  
  
 To create, modify, or delete roles, use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. You can only delete roles that are not used.  
  
 To assign users and groups to the roles that you create, use Report Manager. For more information, see [Grant User Access to a Report Server (Report Manager)](../../Topics/TopicNameContainA/Grant-User-Access-to-a-Report-Server--Report-Manager-.md).  
  
> [!NOTE]  
>  If the report server is configured for SharePoint integrated mode, and you connected to the SharePoint site that the report server is integrated with, you can view and modify the permission levels that control access to report server content and operations.  
  
### To create a role definition  
  
1.  In Object Explorer, expand a report server node.  
  
2.  Expand the Security folder.  
  
3.  If you are creating an item-level role definition, right-click **Roles**, and point to **New Role**.  
  
     Or, if you are creating a system-level role definition, right-click **System Roles**, and point to **New System Role**.  
  
4.  Type a unique name for the role. A name must contain at least one character. It can also include spaces and certain symbols, but not the characters ; ? : @ & = + , $ / * < > &#124; " or /.  
  
5.  Optionally type a description. In [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] this description is visible only on this page. Users who view this item through Report Manager can see this description in that tool.  
  
6.  Select the tasks that members of this role can perform.  
  
7.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
### To delete or modify a role definition  
  
1.  In Object Explorer, expand a report server node.  
  
2.  Expand the Security folder.  
  
3.  To delete or modify an item-level role definition, expand the Roles folder. Perform one of the following:  
  
    1.  To delete a role definition, right-click the item and click **Delete**. The **Delete Object** dialog box is displayed. [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
    2.  To modify a role definition, right-click the item and click **Properties**. The General page of the **User Role Properties** dialog box is displayed.  
  
         Select the tasks that members of this role can perform, and click **OK**.  
  
4.  To delete or modify a system-level role definition, expand the **System Roles** folder. Perform one of the following:  
  
    1.  To delete a system role definition, right-click the item and click **Delete**. The **Delete Object** dialog box is displayed. [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
    2.  To modify a system role definition, right-click the item and click **Properties**. The General page of the **System Role Properties** dialog box is displayed.  
  
         Select the tasks that members of this role can perform, and click **OK** to apply the changes.  
  
## See Also  
 [Connect to a Report Server in Management Studio](../../Topics/TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Create and Manage Role Assignments](../../Topics/TopicNameNotContainA/Create-and-Manage-Role-Assignments.md)   
 [Reporting Services in SQL Server Management Studio (SSRS)](../../Topics/TopicNameNotContainA/Reporting-Services-in-SQL-Server-Management-Studio--SSRS-.md)