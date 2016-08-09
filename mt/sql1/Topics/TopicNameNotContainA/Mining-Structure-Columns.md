---
title: "Mining Structure Columns"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
caps.latest.revision: 42
manager: paulettm
---
# Mining Structure Columns
You define the columns in a mining structure when you create the mining structure, by choosing columns of external data and then specifying how the data is to be used for modeling. Therefore, mining structure columns are more than copies of data from a data source: they define how the data from the source is to be used by the mining model. You can assign properties that determine how the data is discretized, properties that describe how the data values are distributed  
  
 Mining structure columns are designed to be flexible and extensible, because each algorithm that you use to build a mining model may use different columns from the structure to interpret the data. Rather than have one set of data for each model, you can use a single mining structure and use the columns in it to customize the data for each model.  
  
## Defining Mining Structure Columns  
 The basic data types and content types that define structure columns are derived from the data source that you use to create the structure. You can change these settings within the mining structure, and you can also set modeling flags and set the distribution for continuous columns.  
  
 The definition of a mining structure column must contain the following information:  
  
-   **ID**: The unique name of the column, often the same as the name. This cannot be changed after you create the mining structure, whereas the name can be changed.  
  
-   **Name**: A name or alias for the column.  
  
-   **Content**: An enumeration that describes whether the data is discrete or continuous.  
  
-   **Type**: An enumeration that indicates the general data type.  
  
-   **Distribution**: An enumeration that describes the expected distribution of values. A distribution is included if the column is continuous.  
  
-   **Modeling flags**: An enumeration that indicates how to handle missing values and so forth. Modeling flags can also be defined on the mining model, but the model flags are different than the flags used on structure columns.  
  
-   **Bindings**: Properties that specify the source data.  
  
 Third-party algorithms may also include custom properties that can be defined on the mining structure column.  
  
 For more information about the data mining structure and the data mining model, see [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md).  
  
## Related Content  
 See the following topics for more information about how to define and use mining structure columns.  
  
|Topic|Links|  
|-----------|-----------|  
|Describes the data types that you can use to define a mining structure column.|[Data Types (Data Mining)](../../Topics/TopicNameNotContainA/Data-Types--Data-Mining-.md)|  
|Describes the content types that are available for each type of data that is contained in a mining structure column. Content types are dependent on data type. The content type is assigned at the model level, and determines how the column data is used by the model.|[Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md)|  
|Introduces the concept of nested tables, and explains how nested tables can be added to the data source as mining structure columns.|[Classified Columns (Data Mining)](../../Topics/TopicNameNotContainA/Classified-Columns--Data-Mining-.md)|  
|Lists and explains the distribution properties that you can set on a mining structure column to specify the expected distribution of values in the column.|[Column Distributions (Data Mining)](../../Topics/TopicNameNotContainA/Column-Distributions--Data-Mining-.md)|  
|Explains the concept of discretization (sometimes referred to as *binning*) and describes the methods that Analysis Services provides for discretizing continuous numeric data.|[Discretization Methods (Data Mining)](../../Topics/TopicNameNotContainA/Discretization-Methods--Data-Mining-.md)|  
|Describes the modeling flags that you can set on a mining structure column.|[Modeling Flags (Data Mining)](../../Topics/TopicNameNotContainA/Modeling-Flags--Data-Mining-.md)|  
|Describes classified columns, which are a special type of column that you can use to relate one mining structure column to another.|[Classified Columns (Data Mining)](../../Topics/TopicNameNotContainA/Classified-Columns--Data-Mining-.md)|  
|Learn to add and modify mining structure columns.|[Mining Structure Tasks and How-tos](../../Topics/TopicNameNotContainA/Mining-Structure-Tasks-and-How-tos.md)|  
  
## See Also  
 [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md)   
 [Mining Model Columns](../../Topics/TopicNameNotContainA/Mining-Model-Columns.md)