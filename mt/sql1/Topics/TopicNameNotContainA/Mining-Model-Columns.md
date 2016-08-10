---
title: "Mining Model Columns"
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
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
caps.latest.revision: 39
caps.handback.revision: 0
manager: paulettm
---
# Mining Model Columns
A data mining model applies a mining model algorithm to the data that is represented by a mining structure. Like the mining structure, the mining model contains columns. A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure. The model can use all the columns that the mining structure contains or a subset of the columns.  
  
 You can define two additional pieces of information on a mining model column: usage, and modeling flags.  
  
-   **Usage** is a property that defines how the model uses the column. Columns can be used as input columns, key columns, or predictable columns.  
  
-   **Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model. You can define modeling flags programmatically by using the Data Mining Extensions (DMX) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
 The following list describes the modeling flags that you can define on a mining model column.  
  
 **MODEL_EXISTENCE_ONLY**  
 Indicates that the presence of the attribute is more important than the values that are in the attribute column. For example, consider a case table that contains a list of order items that are associated with a particular customer. The table data includes the product type, ID, and cost of each item. For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself. In this case, the cost column should be marked as **MODEL_EXISTENCE_ONLY**.  
  
 **REGRESSOR**  
 Indicates that the algorithm can use the specified column in the regression formula of regression algorithms. This flag is supported by the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Decision Trees and [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Time Series algorithms.  
  
 For more information about setting the usage property and defining modeling flags programmatically with DMX, see [Mining Structure Columns](assetId:///43e4b591-7b34-494c-9b2d-7f0fe69af788). For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], see [Moving Data Mining Objects](../../Topics/TopicNameNotContainA/Moving-Data-Mining-Objects.md).  
  
## See Also  
 [Data Mining Algorithms (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md)   
 [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md)   
 [Change the Properties of a Mining Model](../../Topics/TopicNameContainA/Change-the-Properties-of-a-Mining-Model.md)   
 [Exclude a Column from a Mining Model](../../Topics/TopicNameContainA/Exclude-a-Column-from-a-Mining-Model.md)   
 [Mining Structure Columns](../../Topics/TopicNameNotContainA/Mining-Structure-Columns.md)