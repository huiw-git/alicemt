---
title: Assign Hierarchy Member Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
---
# Assign Hierarchy Member Permissions (Master Data Services)
  Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
 Hierarchy member permissions are optional. They provide added granularity to model object permissions, which are required.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To assign hierarchy member permissions  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
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
    >  Hierarchy member permissions do not take effect immediately. See [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../Topic/Immediately%20Apply%20Member%20Permissions%20\(Master%20Data%20Services\).md) for more information.  
  
## See Also  
 [Delete Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Delete%20Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)  
  
  