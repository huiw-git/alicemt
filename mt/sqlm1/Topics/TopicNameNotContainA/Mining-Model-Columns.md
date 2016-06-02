---
title: Mining Model Columns
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
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
---
# Mining Model Columns
  A data mining model applies a mining model algorithm to the data that is represented by a mining structure. Like the mining structure, the mining model contains columns. A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure. The model can use all the columns that the mining structure contains or a subset of the columns.  
  
 You can define two additional pieces of information on a mining model column: usage, and modeling flags.  
  
-   **Usage** is a property that defines how the model uses the column. Columns can be used as input columns, key columns, or predictable columns.  
  
-   **Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model. You can define modeling flags programmatically by using the Data Mining Extensions \(DMX\) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
 The following list describes the modeling flags that you can define on a mining model column.  
  
 **MODEL\_EXISTENCE\_ONLY**  
 Indicates that the presence of the attribute is more important than the values that are in the attribute column. For example, consider a case table that contains a list of order items that are associated with a particular customer. The table data includes the product type, ID, and cost of each item. For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself. In this case, the cost column should be marked as **MODEL\_EXISTENCE\_ONLY**.  
  
 **REGRESSOR**  
 Indicates that the algorithm can use the specified column in the regression formula of regression algorithms. This flag is supported by the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Decision Trees and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Time Series algorithms.  
  
 For more information about setting the usage property and defining modeling flags programmatically with DMX, see [CREATE MINING MODEL &#40;DMX&#41;](../Topic/CREATE%20MINING%20MODEL%20\(DMX\).md). For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], see [Moving Data Mining Objects](../../Topics\TopicNameNotContainA/Moving-Data-Mining-Objects.md).  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Change the Properties of a Mining Model](../../Topics\TopicNameContainA/Change-the-Properties-of-a-Mining-Model.md)   
 [Exclude a Column from a Mining Model](../../Topics\TopicNameContainA/Exclude-a-Column-from-a-Mining-Model.md)   
 [Mining Structure Columns](../../Topics\TopicNameNotContainA/Mining-Structure-Columns.md)  
  
  