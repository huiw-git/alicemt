---
title: Derived Hierarchies (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
---
# Derived Hierarchies (Master Data Services)
  A [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.  
  
 You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.  
  
## Leaf Members Group Other Leaf Members  
 In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity. A derived hierarchy is based on the relationship between these entities. An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.  
  
 You can change the structure of a derived hierarchy without affecting the underlying data. As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.  
  
## Explicit Hierarchies versus Derived Hierarchies  
 The following table shows some of the differences between explicit and derived hierarchies.  
  
> [!NOTE]  
>  Explicit Hierarchies are deprecated in this release of [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)].  
  
|Explicit Hierarchies|Derived Hierarchies|  
|--------------------------|-------------------------|  
|Structure is defined by the user|Structure is derived from the relationships between domain-based attributes|  
|Contains members from a single entity|Contains members from multiple entities|  
|Uses consolidated members to group other members|Uses leaf members from one entity to group leaf members from another entity|  
  
## Creating a Variable-Depth Hierarchy  
 There are two recommended ways to create a variable-depth hierarchy:  
  
-   If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.  
  
-   If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy. For the leaf entity, use a domain-based attribute that is based upon the parent entity. For the parent entity, use a domain-based attribute that is based upon itself.  
  
## Derived Hierarchy Example  
 In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity. This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.  
  
 The hierarchy structure shows how the members are grouped. The entity with the most members is at the bottom.  
  
 ![Hierarchy Derived from Model Structure](../../Topics/TopicNameNotContainA/media/mds_conc_derived_hierarchy_structure.gif "mds_conc_derived_hierarchy_structure")  
  
 In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category. When you view the members in this hierarchy, each level in the tree contains members from the same entity.  
  
 ![Mountain Bike Derived Hierarchy Example](../../Topics/TopicNameNotContainA/media/mds_conc_derived_hierarchy_example.gif "mds_conc_derived_hierarchy_example")  
  
 This type of hierarchy prevents you from moving a member to a level that is not valid. For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes. You cannot move Road-650 directly under a category, like 1 {Bikes}. Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.  
  
## Notes  
 All members in a derived hierarchy tree are sorted by code. You cannot change the sort order.  
  
 If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy. Create business rules to require attributes to be populated. For more information, see [Require Attribute Values &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Require-Attribute-Values--Master-Data-Services-.md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new derived hierarchy.|[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Derived-Hierarchy--Master-Data-Services-.md)|  
|Hide or delete levels in an existing derived hierarchy.|[Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Hide-or-Delete-Levels-in-a-Derived-Hierarchy--Master-Data-Services-.md)|  
|Change the name of an existing derived hierarchy.|[Change a Derived Hierarchy Name &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Change-a-Derived-Hierarchy-Name--Master-Data-Services-.md)|  
|Delete an existing derived hierarchy.|[Delete a Derived Hierarchy &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Delete-a-Derived-Hierarchy--Master-Data-Services-.md)|  
  
## Related Content  
  
-   [Domain-Based Attributes &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Domain-Based-Attributes--Master-Data-Services-.md)  
  
-   [Explicit Hierarchies &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Explicit-Hierarchies--Master-Data-Services-.md)  
  
-   [Recursive Hierarchies &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Recursive-Hierarchies--Master-Data-Services-.md)  
  
-   [Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Derived-Hierarchies-with-Explicit-Caps--Master-Data-Services-.md)  
  
-   [Show Many-to-Many Relationships in Derived Hierarchies &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Show-Many-to-Many-Relationships-in-Derived-Hierarchies--Master-Data-Services-.md)  
  
-   [Collections &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Collections--Master-Data-Services-.md)  
  
  