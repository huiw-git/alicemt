---
title: "Delete Users or Groups (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Delete Users or Groups (Master Data Services)
Delete users or groups when you no longer want them to access [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
 Note the following behavior when deleting users and groups:  
  
-   If you delete a user who is a member of a group that has access to [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], then the user can still access [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] until you remove the user from the Active Directory or local group.  
  
-   If you delete a group, all users from the group who have accessed [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] are displayed in the **Users** list until you delete them.  
  
-   Changes to security are not propagated to the MDS [!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)] for 20 minutes.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
### To delete users or groups  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  To delete a user, remain on the **Users** page. To delete a group, from the menu bar, click **ManageGroups.**  
  
3.  In the grid,select the row for the user or group that you want to delete.  
  
4.  Click **Delete selected user** or **Delete selected group**.  
  
5.  On the confirmation dialog box, click **OK**.  
  
## See Also  
 [Security (Master Data Services)](../../Topics/TopicNameNotContainA/Security--Master-Data-Services-.md)