---
title: Add Attributes to a Change Tracking Group (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
---
# Add Attributes to a Change Tracking Group (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], add attributes to a change tracking group when you want to track changes to the attribute's values.  
  
> [!NOTE]  
>  After you add an attribute to a change tracking group, when values for the attribute change, the attribute is flagged as changed in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. Create a business rule to take action based on the change.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   Attributes must exist to add to the change tracking group. For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Text%20Attribute%20\(Master%20Data%20Services\).md).  
  
### To add attributes to a change tracking group  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, select the row for the entity that you want to create an attribute for.  
  
4.  Click **Attributes**.  
  
5.  On the **Manage Attributes** page, do one of the following.  
  
    -   If the attribute is for leaf members, select **Leaf** from the **Member Types** list box.  
  
    -   If the attribute is for consolidated members, select **Consolidated** from the **Member Types** list box.  
  
    -   If the attribute is for collections, select **Collection** from the **Member Types** list box.  
  
6.  Select the row for the attribute you want to edit, and then click **Edit**.  
  
7.  Select the **Enable change tracking** check box.  
  
8.  In the **Change tracking group** box, type a number for the group.  
  
9. Click **Save attribute**.  
  
     For the edited attribute, the **Enable Change Tracking Group** column in the grid is changed to **Yes \(Group: entered group number\)**.  
  
10. Repeat this procedure for all attributes you want to include in the group. Use the same change tracking group number for each attribute in the group.  
  
## Next Steps  
  
-   [Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;](../Topic/Initiate%20Actions%20Based%20on%20Attribute%20Value%20Changes%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Create a Text Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Text%20Attribute%20\(Master%20Data%20Services\).md)   
 [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md)  
  
  