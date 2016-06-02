---
title: Delete an Attribute (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
robots: noindex,nofollow
---
# Delete an Attribute (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], delete an attribute when you want to permanently delete the attribute and all associated attribute values.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To delete an attribute  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, select the row for the entity that you want to create an attribute for.  
  
4.  Click **Attributes**.  
  
5.  On the **Manage Attributes** page, do one of the following.  
  
    -   If the attribute is for leaf members, select **Leaf** from the **Member Types** list box.  
  
    -   If the attribute is for consolidated members, select **Consolidated** from the **Member Types** list box.  
  
    -   If the attribute is for collections, select **Collection** from the **Member Types** list box.  
  
6.  Select the row for the attribute you want to delete.  
  
    > [!NOTE]  
    >  You cannot delete the Name or Code attributes.  
  
7.  Click **Delete**.  
  
8.  In the confirmation dialog box, click **OK**.  
  
## See Also  
 [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)   
 [Domain-Based Attributes &#40;Master Data Services&#41;](../Topic/Domain-Based%20Attributes%20\(Master%20Data%20Services\).md)   
 [Create a Text Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Text%20Attribute%20\(Master%20Data%20Services\).md)   
 [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md)  
  
  