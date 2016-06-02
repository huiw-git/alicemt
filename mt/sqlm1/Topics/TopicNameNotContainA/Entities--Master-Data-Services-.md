---
title: Entities (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
---
# Entities (Master Data Services)
  Entities are objects that are contained in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] models. Each entity contains members, which are the rows of master data that you manage.  
  
## How Many Entities are Appropriate?  
 Models can contain as many entities as you want to manage. Each entity should group a similar kind of data. For example, you might want an entity for all of your corporate accounts, or an entity for your master list of employees.  
  
 Typically, there are one or more central entities that are important to your business, and to which other objects in the model relate. For example, in a Product model, you could have a central entity called Product and entities called Subcategory and Category that relate to the Product entity. However, you do not need to have a central entity. Depending on your needs, you might have several entities that you consider to be of equal importance.  
  
## How Entities Relate to Other Model Objects  
 You can think of an entity as a table that contains master data, where the rows represent members and the columns represent attributes.  
  
 ![Master Data Services Entity Represented as Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table.gif "mds_conc_entity_table")  
  
 You populate the entity with a list of master data that you want to manage.  
  
 Entities can be used to build derived hierarchies, which are level\-based hierarchies based on multiple entities. For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20\(Master%20Data%20Services\).md).  
  
 Entities can also be enabled to contain explicit hierarchies \(ragged structures based on a single entity\) and collections \(one\-off combinations of subsets of members\). For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md) and [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md).  
  
## Using Entities as Constrained Lists  
 When users are assigning attributes to the members in an entity, you can have them choose from a constrained list of values. To do this, you use an entity to populate the list of values for the attribute. This is called a domain\-based attribute. For more information, see [Domain-Based Attributes &#40;Master Data Services&#41;](../Topic/Domain-Based%20Attributes%20\(Master%20Data%20Services\).md).  
  
## Base Entities  
 A base entity is a starting point for users when navigating objects in the model. A base entity determines the layout of the screen when a user opens the **Explorer** functional area and clicks **Explorer** on the menu bar. To specify an entity as a base entity, navigate to the **System Administration** functional area. On the **Model View** page, drag the entity from the tree control on the right to the name of the model in the tree control on the left.  
  
## Entity Security  
 You can give users permission to an entity, which includes related model objects. For more information, see [Entity Permissions &#40;Master Data Services&#41;](../Topic/Entity%20Permissions%20\(Master%20Data%20Services\).md).  
  
## Entity Examples  
 The following example shows an entity that has these attributes: Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto. These attributes describe the members. Each member is represented by a single row of attribute values.  
  
 ![Bike Product Entity Table](../../Images\Image\ImageNotContaina/mds_conc_entity_table_w_data.gif "mds_conc_entity_table_w_data")  
  
 In the following example, the Product entity is the central entity. The Subcategory entity is a domain\-based attribute of the Product entity. The Category entity is a domain\-based attribute of the Subcategory entity. StandardCost and ListPrice are free\-form attributes of the Product entity, and FilePhoto is a file attribute of the Product entity.  
  
 ![Product Entity Tree Structure](../../Images\Image\ImageNotContaina/mds_conc_entity_UI.gif "mds_conc_entity_UI")  
  
> [!NOTE]  
>  This is an example based on the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface \(UI\). The hierarchical tree structure shows relationships between entities and domain\-based attributes. It is intended to show relationships rather than represent levels of importance.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a new entity.|[Create an Entity &#40;Master Data Services&#41;](../Topic/Create%20an%20Entity%20\(Master%20Data%20Services\).md)|  
|Change the name of an existing entity.|[Edit an Entity &#40;Master Data Services&#41;](../Topic/Edit%20an%20Entity%20\(Master%20Data%20Services\).md)|  
|Delete an existing entity.|[Delete an Entity &#40;Master Data Services&#41;](../Topic/Delete%20an%20Entity%20\(Master%20Data%20Services\).md)|  
|Assign permission to entities.|[Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Models &#40;Master Data Services&#41;](../Topic/Models%20\(Master%20Data%20Services\).md)  
  
-   [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md)  
  
-   [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)  
  
  