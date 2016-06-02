---
title: Create an Entity Administrator (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
---
# Create an Entity Administrator (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], create an entity administrator when you want a group or user to have all permissions to all objects in one or more entities, or have the permission to approve pending change sets.  
  
> [!TIP]  
>  To simplify administration, create a Windows or local group and configure it as an entity administrator. You can then add and remove users from the group without accessing [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **User and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
## To create an Entity Administrator  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  Select the row for the user or group that you want to edit, and then click **Edit selected user**.  
  
3.  Click the **Models** tab, optionally select a model from the **Models** list and then click **Edit**.  
  
4.  Click the entity you want to grant permissions to, and then click **Admin** on the menu.  
  
5.  Complete step 4 for each entity that you want the group or user to be an administrator for.  
  
6.  Click **Save**.  
  
## See Also  
 [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md)   
 [Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../Topic/Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)  
  
  