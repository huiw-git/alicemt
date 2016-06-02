---
title: Delete an Explicit Hierarchy (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
---
# Delete an Explicit Hierarchy (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], delete an explicit hierarchy when you no longer need it.  
  
> [!WARNING]  
>  When you delete an explicit hierarchy, all consolidated members in the hierarchy are deleted also. If you delete all explicit hierarchies for an entity, all collections for the entity are also deleted and the entity is no longer enabled for explicit hierarchies and collections.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To delete an explicit hierarchy  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, from the grid, select the row for the entity that contains the explicit hierarchy you want to delete.  
  
4.  Click **Explicit Hierarchies**.  
  
5.  On the **Manage Explicit Hierarchy** page, click the explicit hierarchy you want to delete.  
  
6.  Click **Edit**.  
  
7.  In the confirmation dialog box, click **OK**.  
  
## See Also  
 [Create an Explicit Hierarchy &#40;Master Data Services&#41;](../Topic/Create%20an%20Explicit%20Hierarchy%20\(Master%20Data%20Services\).md)   
 [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
  