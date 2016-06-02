---
title: Members (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
---
# Members (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], members are the physical master data. For example, a member can be a Road\-150 bike in a Product entity or a specific customer in a Customer entity.  
  
## How Members Relate to Other Model Objects  
 You can think of members as rows in a table. Related members are contained in an entity, and each member is defined by attribute values.  
  
 In this example, the table represents an entity, the rows in the table represent members, and the columns in the table represent attributes. Each cell represents an attribute value for a specific member.  
  
 ![Master Data Services Entity Represented as Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table.gif "mds_conc_entity_table")  
  
## Member Types  
 There are three types of members: leaf members, consolidated members, and collection members.  
  
 Leaf members are the default members in an entity.  
  
-   In derived hierarchies, leaf members are the only type of member. Leaf members from one entity are used as parents of leaf members from another entity.  
  
-   In explicit hierarchies, leaf members are the lowest level and cannot have children.  
  
 Consolidated members exist only when explicit hierarchies and collections are enabled for the entity.  
  
-   Derived hierarchies do not contain consolidated members.  
  
-   In explicit hierarchies, consolidated members can be parents of other members within the hierarchy, or they can be children.  
  
## Use Hierarchies and Collections to Organize Members  
 Hierarchies and collections can be used to group members for reporting or analysis. For more information, see [Hierarchies &#40;Master Data Services&#41;](../Topic/Hierarchies%20\(Master%20Data%20Services\).md) and [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md).  
  
## Member Example  
 In the following example, each member is made up of a Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto attribute value.  
  
 ![Bike Product Entity Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table_w_data.gif "mds_conc_entity_table_w_data")  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new leaf member.|[Create a Leaf Member &#40;Master Data Services&#41;](../Topic/Create%20a%20Leaf%20Member%20\(Master%20Data%20Services\).md)|  
|Create a new consolidated member.|[Create a Consolidated Member &#40;Master Data Services&#41;](../Topic/Create%20a%20Consolidated%20Member%20\(Master%20Data%20Services\).md)|  
|Delete an existing member or collection.|[Delete a Member or Collection &#40;Master Data Services&#41;](../Topic/Delete%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md)|  
|Reactivate a deleted member or collection.|[Reactivate a Member or Collection &#40;Master Data Services&#41;](../Topic/Reactivate%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md)|  
|Update the attribute values of a member.|[Change the Attribute Type &#40;MDS Add-in for Excel&#41;](../Topic/Change%20the%20Attribute%20Type%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Move members within a hierarchy.|[Move Members within a Hierarchy &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Fix merge conflicts.|[Merge Conflicts &#40;Master Data Services&#41;](../Topic/Merge%20Conflicts%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Master Data Services Overview &#40;MDS&#41;](../Topic/Master%20Data%20Services%20Overview%20\(MDS\).md)  
  
-   [Entities &#40;Master Data Services&#41;](../Topic/Entities%20\(Master%20Data%20Services\).md)  
  
-   [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)  
  
-   [Hierarchies &#40;Master Data Services&#41;](../Topic/Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md)  
  
-   [Leaf Permissions &#40;Master Data Services&#41;](../Topic/Leaf%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [Consolidated Permissions &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [Filter Operators &#40;Master Data Services&#41;](../Topic/Filter%20Operators%20\(Master%20Data%20Services\).md)  
  
  