---
title: "Attribute Groups (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Attribute Groups (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], attribute groups help organize attributes in an entity. When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application.  
  
## How Attribute Groups Change the Display  
 Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
 When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes. To prevent this scrolling, you can create attribute groups.  
  
-   Attribute groups always include the Name and Code attributes.  
  
-   Each attribute for an entity can belong to one or more attribute groups.  
  
-   All attributes are automatically included on the **All Attributes** tab in **Explorer**.  
  
-   There is no way to hide the **All Attributes** tab.  
  
 Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
## Show or Hide Attribute Groups  
 When you create an attribute group, it is automatically hidden from all users except the one who created it. For more information about making the group visible, see [Make an Attribute Group Visible to Users (Master Data Services)](../../Topics/TopicNameNotContainA/Make-an-Attribute-Group-Visible-to-Users--Master-Data-Services-.md).  
  
 If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute. For more information, see [Leaf Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Leaf-Permissions--Master-Data-Services-.md) or [Consolidated Permissions (Master Data Services)](assetId:///084055a3-5fd3-43f3-b620-ac6afab42a3d).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new attribute group and add attributes to it.|[Create an Attribute Group (Master Data Services)](../../Topics/TopicNameNotContainA/Create-an-Attribute-Group--Master-Data-Services-.md)|  
|Make an attribute group visible to users.|[Make an Attribute Group Visible to Users (Master Data Services)](../../Topics/TopicNameNotContainA/Make-an-Attribute-Group-Visible-to-Users--Master-Data-Services-.md)|  
|Change the name of an existing attribute group.|[Change an Attribute Group Name (Master Data Services)](../../Topics/TopicNameNotContainA/Change-an-Attribute-Group-Name--Master-Data-Services-.md)|  
|Delete an existing attribute group.|[Delete an Attribute Group (Master Data Services)](../../Topics/TopicNameNotContainA/Delete-an-Attribute-Group--Master-Data-Services-.md)|  
  
## Related Content  
  
-   [Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Attributes--Master-Data-Services-.md)