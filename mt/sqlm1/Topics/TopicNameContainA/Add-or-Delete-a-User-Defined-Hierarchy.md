---
title: Add or Delete a User-Defined Hierarchy
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
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
---
# Add or Delete a User-Defined Hierarchy
  You add a user\-defined hierarchy to or remove a user\-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
 When you add a user\-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance and the dimension is processed. For more information, see [Multidimensional Model Databases &#40;SSAS&#41;](../Topic/Multidimensional%20Model%20Databases%20\(SSAS\).md) and [Processing a multidimensional model &#40;Analysis Services&#41;](../Topic/Processing%20a%20multidimensional%20model%20\(Analysis%20Services\).md).  
  
### To add a user\-defined hierarchy to a dimension  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, and then open the dimension with which you want to work.  
  
     The dimension opens in Dimension Designer on the **Dimension Structure** tab.  
  
2.  From the **Attributes** pane, drag an attribute that you want to use in the user\-defined hierarchy to the **Hierarchies** pane.  
  
3.  Drag additional attributes to form levels in the user\-defined hierarchy.  
  
     The order in which attributes are listed in the hierarchy is important. For example, in a time hierarchy, years should appear higher in the hierarchy list than days.  
  
4.  Optionally, rearrange the levels in the user\-defined hierarchy by dragging them to the correct positions.  
  
5.  Optionally, modify properties of the user\-defined hierarchy or its levels.  
  
     For example, you might want to specify a name for the user\-defined hierarchy, rename one or more of its levels, and define a custom name for the All level. For more information, see [User Hierarchy Properties](../Topic/User%20Hierarchy%20Properties.md), and [Level Properties - user hierarchies](../Topic/Level%20Properties%20-%20user%20hierarchies.md).  
  
    > [!NOTE]  
    >  By default, a user\-defined hierarchy is just a path that enables users to drill down for information. However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels. For more information, see [Attribute Relationships](../Topic/Attribute%20Relationships.md) and [Define Attribute Relationships](../../Topics\TopicNameNotContainA/Define-Attribute-Relationships.md).  
  
### To remove a user\-defined hierarchy from a dimension  
  
-   On the **Dimension Structure** tab, click the user\-defined hierarchy that you want to remove in the **Hierarchies** pane. On the toolbar, click **Delete**.  
  
     — or —  
  
-   Right\-click the user\-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.  
  
     — or —  
  
-   Drag the user\-defined hierarchy off of the design surface.  
  
## See Also  
 [User Hierarchies](../Topic/User%20Hierarchies.md)   
 [Create User-Defined Hierarchies](../../Topics\TopicNameNotContainA/Create-User-Defined-Hierarchies.md)  
  
  