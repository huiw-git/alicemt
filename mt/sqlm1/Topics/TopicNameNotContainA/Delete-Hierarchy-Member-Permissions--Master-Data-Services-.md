---
title: Delete Hierarchy Member Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
---
# Delete Hierarchy Member Permissions (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], delete model object permissions to remove any assignments that have been made.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To delete hierarchy member permissions  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  On the **Users** or **Groups** page, select the row for the user or group that you want to edit.  
  
3.  Click **Edit selected user**.  
  
4.  Click the **Hierarchy Members** tab.  
  
5.  From the **Model** list, select a model.  
  
6.  From the **Version** list, select a version.  
  
7.  Click **Edit**.  
  
8.  Find the tree node with the permission, in the **Hierarchy Member Permissions** panel.  
  
9. Click the tree node, and click **None** in the context menu.  
  
    > [!NOTE]  
    >  You cannot remove a permission from a user if the permission is inherited from a group. You must remove the permission from the group instead.  
  
10. Click **Save**.  
  
## See Also  
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)  
  
  