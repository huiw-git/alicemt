---
title: Derived Hierarchies with Explicit Caps (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
---
# Derived Hierarchies with Explicit Caps (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], when the levels from an explicit hierarchy are used as the top levels of a derived hierarchy, this is called a derived hierarchy with an explicit cap.  
  
 The explicit hierarchy must be based on the same entity as the entity at the top of the derived hierarchy.  
  
 In the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface \(UI\), you create this type of hierarchy by dragging an explicit hierarchy to the top of a derived hierarchy.  
  
 ![mds_conc_explicit_cap_UI_structure](../../Images\Image\ImageNotContaina/mds_conc_explicit_cap_UI_structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## Derived Hierarchy with Explicit Cap Example  
 In this example, the members in the explicit hierarchy are from the Subcategory entity. In the derived hierarchy, the top\-level members are also from the Subcategory entity.  
  
 ![mds_conc_explicit_cap_UI_example](../../Images\Image\ImageNotContaina/mds_conc_explicit_cap_UI_example.gif "mds_conc_explicit_cap_UI_example")  
  
 By using the explicit hierarchy at the top of a derived hierarchy, the derived hierarchy becomes ragged.  
  
## Rules  
  
-   You cannot have more than one explicit hierarchy in a derived hierarchy with explicit cap.  
  
-   You can use the same explicit hierarchy as a cap for multiple derived hierarchies.  
  
-   You cannot assign hierarchy member permissions to derived hierarchies with explicit caps. If you assign permissions to either the explicit hierarchy or the derived hierarchy individually, the permissions affect both hierarchies.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a derived hierarchy.|[Create a Derived Hierarchy &#40;Master Data Services&#41;](../Topic/Create%20a%20Derived%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Create an explicit hierarchy.|[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../Topic/Create%20an%20Explicit%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|Delete an existing derived hierarchy.|[Delete a Derived Hierarchy &#40;Master Data Services&#41;](../Topic/Delete%20a%20Derived%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|||  
  
## Related Content  
  
-   [Derived Hierarchies &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
  