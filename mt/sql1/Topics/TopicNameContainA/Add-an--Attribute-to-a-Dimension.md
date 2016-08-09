---
title: "Add an  Attribute to a Dimension"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 31
manager: mblythe
---
# Add an  Attribute to a Dimension
You can add an attribute to a dimension either automatically or manually in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].  
  
 To create an attribute automatically, on the **Dimension Structure** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], select the column that you want to map to an attribute, and then drag that column from the **Data Source View** pane to the **Attributes** pane. This creates an attribute that is mapped to the column, and assigns the same name to the attribute as the name of the column. If an attribute that uses that name already exists, [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] adds an ordinal number suffix, starting with "1" for the first duplicate name.  
  
 To create an attribute manually, set the **Attributes** pane to grid view. In the name column of the last row in the grid, click the **<new attribute\>** item. Type a name for the new attribute. This creates an attribute that is not mapped to a column and that has default settings for all its properties. You can set the mapping in the **Properties** window of [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] by configuring the **KeyColumns** property for the new attribute.  
  
 For more information, see [Define a New Attribute Automatically](../../Topics/TopicNameContainA/Define-a-New-Attribute-Automatically.md), [How to create a new attribute manually](assetId:///554ea10e-b0b0-4987-add8-19113d824787), [Bind an Attribute to a Name Column](../../Topics/TopicNameContainA/Bind-an-Attribute-to-a-Name-Column.md), and [Modify the KeyColumn Property of an Attribute](../../Topics/TopicNameNotContainA/Modify-the-KeyColumn-Property-of-an-Attribute.md).  
  
## See Also  
 [Dimension Attribute Properties Reference](../../Topics/TopicNameNotContainA/Dimension-Attribute-Properties-Reference.md)