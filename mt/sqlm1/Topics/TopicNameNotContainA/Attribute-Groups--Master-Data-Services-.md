---
title: Attribute Groups (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
---
# Attribute Groups (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], attribute groups help organize attributes in an entity. When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.  
  
## How Attribute Groups Change the Display  
 Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
 When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes. To prevent this scrolling, you can create attribute groups.  
  
-   Attribute groups always include the Name and Code attributes.  
  
-   Each attribute for an entity can belong to one or more attribute groups.  
  
-   All attributes are automatically included on the **All Attributes** tab in **Explorer**.  
  
-   There is no way to hide the **All Attributes** tab.  
  
 Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
## Show or Hide Attribute Groups  
 When you create an attribute group, it is automatically hidden from all users except the one who created it. For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](../Topic/Make%20an%20Attribute%20Group%20Visible%20to%20Users%20\(Master%20Data%20Services\).md).  
  
 If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute. For more information, see [Leaf Permissions &#40;Master Data Services&#41;](../Topic/Leaf%20Permissions%20\(Master%20Data%20Services\).md) or [Consolidated Permissions &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new attribute group and add attributes to it.|[Create an Attribute Group &#40;Master Data Services&#41;](../Topic/Create%20an%20Attribute%20Group%20\(Master%20Data%20Services\).md)|  
|Make an attribute group visible to users.|[Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](../Topic/Make%20an%20Attribute%20Group%20Visible%20to%20Users%20\(Master%20Data%20Services\).md)|  
|Change the name of an existing attribute group.|[Change an Attribute Group Name &#40;Master Data Services&#41;](../Topic/Change%20an%20Attribute%20Group%20Name%20\(Master%20Data%20Services\).md)|  
|Delete an existing attribute group.|[Delete an Attribute Group &#40;Master Data Services&#41;](../Topic/Delete%20an%20Attribute%20Group%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)  
  
  