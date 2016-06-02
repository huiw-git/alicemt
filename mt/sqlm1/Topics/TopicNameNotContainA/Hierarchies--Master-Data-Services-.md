---
title: Hierarchies (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
---
# Hierarchies (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], a hierarchy is a tree structure that you can use to:  
  
-   Group similar members for organizational purposes.  
  
-   Consolidate and summarize members for reporting and analysis.  
  
## What Hierarchies Contain  
 Each hierarchy contains members from one or more entities. When a member is added, changed, or deleted, all hierarchies are updated. This ensures that the data is accurate in all hierarchies. Hierarchies also help ensure that each member is counted once and only once.  
  
 If you want to create a grouping of a subset of members, consider using a collection. For more information, see [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md).  
  
## Kinds of Hierarchies  
 You can create multiple hierarchies to view and organize your members in different ways. You can create:  
  
-   Ragged hierarchies from a single entity, which are called explicit hierarchies. For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md).  
  
-   Level\-based hierarchies from multiple entities, based on the existing relationships between entities and their attributes, which are called derived hierarchies. For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20\(Master%20Data%20Services\).md).  
  
> [!NOTE]  
>  All members in a hierarchy must be within the same model.  
  
## Hierarchies Are Not Taxonomies  
 A hierarchy is different from a taxonomy. A taxonomy organizes members by multiple attributes at the same time, while a hierarchy organizes members by one attribute at a time. A taxonomy can include the same member multiple times, while a hierarchy includes a member only once.  
  
 For example, the same bike can be included in a taxonomy twice: once because it's red, and once because it's a size 38. In a hierarchy, the bike is included only once, so you must decide whether to show it in relation to its color or its size.  
  
## Hierarchy Example  
 In the following example, product members are grouped by subcategory members.  
  
 ![Hierarchy Grouped by Subcategory Example](../../Images\Image\ImageNotContaina/mds_conc_hierarchy.gif "mds_conc_hierarchy")  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a explicit hierarchy.|[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../Topic/Create%20an%20Explicit%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Create a derived hierarchy.|[Create a Derived Hierarchy &#40;Master Data Services&#41;](../Topic/Create%20a%20Derived%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Hide or delete levels in an existing derived hierarchy.|[Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;](../Topic/Hide%20or%20Delete%20Levels%20in%20a%20Derived%20Hierarchy%20\(Master%20Data%20Services\).md)|  
  
## Related Content  
  
-   [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Derived Hierarchies &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Recursive Hierarchies &#40;Master Data Services&#41;](../Topic/Recursive%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20with%20Explicit%20Caps%20\(Master%20Data%20Services\).md)  
  
-   [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md)  
  
  