---
title: Add a Mining Model to an Existing Mining Structure
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
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
---
# Add a Mining Model to an Existing Mining Structure
  You can add more mining models to a mining structure, after you add the initial model. Each model must contain columns that exist in the structure, but you can define the usage of the columns differently for each mining model. For more information about how to define mining models columns, see [Mining Model Columns](../../Topics\TopicNameNotContainA/Mining-Model-Columns.md).  
  
### To add a mining model to the structure  
  
1.  From the **Mining Model** menu item in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], select **New Mining Model**.  
  
     The **New Mining Model** dialog box opens.  
  
2.  Under **Model name**, enter a name for the new mining model.  
  
3.  Under **Algorithm name**, select the algorithm that the mining model will be built from.  
  
4.  Click **OK**.  
  
 A new mining model appears in the **Mining Models** tab. The model uses the default columns that exist in the structure. For information about how to modify the columns, see [Change the Properties of a Mining Model](../../Topics\TopicNameContainA/Change-the-Properties-of-a-Mining-Model.md).  
  
## See Also  
 [Mining Model Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)  
  
  