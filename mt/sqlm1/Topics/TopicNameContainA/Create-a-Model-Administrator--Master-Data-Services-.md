---
title: Create a Model Administrator (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
---
# Create a Model Administrator (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], create a model administrator when you want a group or user to have all permissions to all objects in one or more models.  
  
> [!TIP]  
>  To simplify administration, create a Windows or local group and configure it as a model adminstrator. You can then add and remove users from the group without accessing [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **User and Group Permissions** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To create a model administrator  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  On the **Users** or **Groups** page, select the row for the user or group that you want to edit.  
  
3.  Click **Edit selected user**.  
  
4.  Click the **Models** tab.  
  
5.  Optionally, select a model from the **Model** list.  
  
6.  Click **Edit**.  
  
7.  Click the model you want to grant permission to.  
  
8.  From the menu, select **Admin**.  
  
9. Complete steps 7 and 8 for each model you want the group or user to be an administrator for.  
  
10. Click **Save**.  
  
## See Also  
 [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md)   
 [Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../Topic/Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)  
  
  