---
title: "Add or Delete a User-Defined Hierarchy"
ms.custom: na
ms.date: 08/09/2016
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
caps.latest.revision: 52
caps.handback.revision: 0
manager: mblythe
---
# Add or Delete a User-Defined Hierarchy
You add a user-defined hierarchy to or remove a user-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
 When you add a user-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance and the dimension is processed. For more information, see [Multidimensional Model Databases (SSAS)](../../Topics/TopicNameNotContainA/Multidimensional-Model-Databases--SSAS-.md) and [Processing a multidimensional model (Analysis Services)](../../Topics/TopicNameContainA/Processing-a-multidimensional-model--Analysis-Services-.md).  
  
### To add a user-defined hierarchy to a dimension  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project, and then open the dimension with which you want to work.  
  
     The dimension opens in Dimension Designer on the **Dimension Structure** tab.  
  
2.  From the **Attributes** pane, drag an attribute that you want to use in the user-defined hierarchy to the **Hierarchies** pane.  
  
3.  Drag additional attributes to form levels in the user-defined hierarchy.  
  
     The order in which attributes are listed in the hierarchy is important. For example, in a time hierarchy, years should appear higher in the hierarchy list than days.  
  
4.  Optionally, rearrange the levels in the user-defined hierarchy by dragging them to the correct positions.  
  
5.  Optionally, modify properties of the user-defined hierarchy or its levels.  
  
     For example, you might want to specify a name for the user-defined hierarchy, rename one or more of its levels, and define a custom name for the All level. For more information, see [Configuring User-defined Hierarchy Properties](assetId:///344af8f8-12f3-48c0-b934-4503779d37ff), and [Configuring Level Properties](assetId:///dabb7335-887b-442a-b67c-4901ba1242b7).  
  
    > [!NOTE]  
    >  By default, a user-defined hierarchy is just a path that enables users to drill down for information. However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels. For more information, see [Attribute Relationships](assetId:///2491422a-4cf5-4b23-b6ab-289222b22ce8) and [Define Attribute Relationships](../../Topics/TopicNameNotContainA/Define-Attribute-Relationships.md).  
  
### To remove a user-defined hierarchy from a dimension  
  
-   On the **Dimension Structure** tab, click the user-defined hierarchy that you want to remove in the **Hierarchies** pane. On the toolbar, click **Delete**.  
  
     — or —  
  
-   Right-click the user-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.  
  
     — or —  
  
-   Drag the user-defined hierarchy off of the design surface.  
  
## See Also  
 [User-defined Hierarchies](assetId:///9394e9a3-2242-4f0e-85e0-25d499d2d3b6)   
 [Create User-Defined Hierarchies](../../Topics/TopicNameNotContainA/Create-User-Defined-Hierarchies.md)