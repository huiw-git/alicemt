---
title: View Attributes in Dimension Designer
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
---
# View Attributes in Dimension Designer
  Attributes are created on dimension objects. You can view and configure attributes by using Dimension Designer in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. The **Attributes** pane of the **Dimension Structure** tab of Dimension Designer lists the attributes that are in a dimension. Use this pane to add, remove, or configure attributes. You can also select attributes to use as a level in a new hierarchy or to add as a level in an existing hierarchy.  
  
 To view the attributes in a dimension, open Dimension Designer for the dimension. The **Attributes** pane of the **Dimension Structure**  tab of the designer shows the attributes that are in the dimension. You can switch between a list, tree, or grid view by pointing to **Show Attributes in** on the **Dimension** menu of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and then clicking one of the following commands:  
  
1.  Show Attributes in a **List**. Displays the attributes in list format. Right\-click an attribute to delete it from the list, to rename the attribute, or to change the usage of the attribute. Use this view for building hierarchies. Attribute information and member properties are not visible.  
  
2.  Show Attributes in a **Tree**. Display the attributes in tree format, with the dimension as the top\-level node in the tree. Expand an attribute to view attribute relationships for it or to create a new attribute relationship, by performing the following actions:  
  
    -   Click the dimension, an attribute, or a member property to view its properties in the **Properties** window.  
  
    -   Right\-click an attribute or a member property to delete it from the list, to rename it, or to change its usage.  
  
     Use this view for viewing and creating member properties. You can also use this view to build hierarchies.  
  
3.  Show Attributes in a **Grid**. Display the attributes in grid format. The grid displays the following columns:  
  
    -   **Name** shows the value of the **Name** property. Type a different name to change the setting.  
  
    -   **Usage** specifies whether this is a Regular, Key, Parent, or AccountType attribute. Click a value in this column to select a different setting.  
  
    -   **Type** specifies the business intelligence category for the attribute. Click this cell to select a different setting.  
  
    -   **Key Column** shows the OLE DB data type for the **KeyColumn** property on the attribute. This column cannot be changed.  
  
    -   **Name Column** indicates whether the **NameColumn** property setting on the attribute is the same column as the setting for the **KeyColumn** property. This column cannot be changed.  
  
     Click any row in the grid to view properties for that attribute.  
  
     Use this view for creating and configuring attributes.  
  
 In [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], the icons shown in the following table mark attributes according to their usage.  
  
|Icon|Attribute Usage|  
|----------|---------------------|  
|![Attribute icon](../../Images\Image\ImageNotContaina/as_icon_attribute.gif "as_icon_attribute")|Regular or AccountType|  
|![Key attribute icon](../../Images\Image\ImageNotContaina/as_icon_key_attribute.gif "as_icon_key_attribute")|Key|  
|![Parent attribute icon](../../Images\Image\ImageNotContaina/as_icon_parent_attribute.gif "as_icon_parent_attribute")|Parent|  
  
## See Also  
 [Dimension Attribute Properties Reference](../../Topics\TopicNameNotContainA/Dimension-Attribute-Properties-Reference.md)  
  
  