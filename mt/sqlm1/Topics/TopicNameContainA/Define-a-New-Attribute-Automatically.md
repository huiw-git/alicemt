---
title: Define a New Attribute Automatically
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
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
---
# Define a New Attribute Automatically
  You can create a new attribute in a dimension by using drag\-and\-drop editing in the Dimension Designer.  
  
### To create a new attribute automatically  
  
1.  In Dimension Designer, open the dimension in which you want to create the attribute.  
  
2.  On the **Dimension Structure** tab, in the **Data Source View** pane, in the table to which you want to bind the attribute, select the column, and then drag the column to the **Attributes** pane.  
  
     [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] creates the new attribute that has the same name as the column to which it is bound. If there are multiple attributes that use the same column, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] appends a number to the attribute name.  
  
## See Also  
 [Dimensions in Multidimensional Models](../../Topics\TopicNameNotContainA/Dimensions-in-Multidimensional-Models.md)   
 [Dimension Attribute Properties Reference](../../Topics\TopicNameNotContainA/Dimension-Attribute-Properties-Reference.md)  
  
  