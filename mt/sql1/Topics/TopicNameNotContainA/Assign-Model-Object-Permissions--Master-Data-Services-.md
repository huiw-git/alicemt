---
title: "Assign Model Object Permissions (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Assign Model Object Permissions (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], assign permissions to model objects when you need to give a user or group access to data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], or when you need to make a user or group an administrator.  
  
> [!NOTE]  
>  When you assign permission to a model, permission to all other models is implicitly denied. If you do not assign model object permissions, the user or group cannot access any data in **Explorer**.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To assign model object permissions  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  On the **Users** or **Groups** page, select the row for the user or group that you want to edit.  
  
3.  Click **Edit selected user**.  
  
4.  Click the **Models** tab.  
  
5.  Optionally, select a model from the **Model** list.  
  
6.  Click **Edit**.  
  
7.  Expand the tree, and click the model object you want to assign permissions to.  
  
8.  From the menu, select a combination of Read, Create, Update and Delete, or Deny.  
  
9. On the top model level, select **Admin** if you need to make a user model administrator.  
  
10. Click **Save**.  
  
## Next Steps  
  
-   (Optional) [Assign Hierarchy Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Assign-Hierarchy-Member-Permissions--Master-Data-Services-.md)  
  
## See Also  
 [Delete Model Object Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Delete-Model-Object-Permissions--Master-Data-Services-.md)   
 [Model Object Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Model-Object-Permissions--Master-Data-Services-.md)   
 [Create a Model Administrator (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Model-Administrator--Master-Data-Services-.md)