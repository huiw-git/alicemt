---
title: "Assign Hierarchy Member Permissions (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Assign Hierarchy Member Permissions (Master Data Services)
Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
 Hierarchy member permissions are optional. They provide added granularity to model object permissions, which are required.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To assign hierarchy member permissions  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  On the **Users** or **Groups** page, select the row for the user or group that you want to edit.  
  
3.  Click **Edit selected user**.  
  
4.  Click the **Hierarchy Members** tab.  
  
5.  From the **Model** list, select a model.  
  
6.  From the **Version** list, select a version.  
  
7.  From the **Hierarchy** list, select a hierarchy.  
  
8.  Click **Edit**.  
  
9. Expand the tree, and click the hierarchy node you want to assign permissions to.  
  
10. From the menu, select a combination of **Create**, **Read,Update** and **Delete** permissions, or **Deny** permissions.  
  
11. Click **Save**.  
  
    > [!NOTE]  
    >  Hierarchy member permissions do not take effect immediately. See [Immediately Apply Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Immediately-Apply-Member-Permissions--Master-Data-Services-.md) for more information.  
  
## See Also  
 [Delete Hierarchy Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Delete-Hierarchy-Member-Permissions--Master-Data-Services-.md)   
 [Assign Model Object Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Assign-Model-Object-Permissions--Master-Data-Services-.md)   
 [Hierarchy Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Hierarchy-Member-Permissions--Master-Data-Services-.md)