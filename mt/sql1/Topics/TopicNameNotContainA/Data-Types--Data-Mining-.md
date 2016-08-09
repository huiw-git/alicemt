---
title: "Data Types (Data Mining)"
ms.custom: na
ms.date: 2016-03-02
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
caps.latest.revision: 48
caps.handback.revision: 0
manager: paulettm
---
# Data Types (Data Mining)
When you create a mining model or a mining structure in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], you must define the data types for each of the columns in the mining structure. The data type tells the analysis engine whether the data in the data source is numerical or text, and how the data should be processed. For example, if your source data contains numerical data, you can specify whether the numbers be treated as integers or by using decimal places.  
  
 [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] supports the following data types for mining structure columns:  
  
|Data Type|Supported Content Types|  
|---------------|-----------------------------|  
|**Text**|Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence|  
|**Long**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|**Boolean**|Cyclical, Discrete, Ordered|  
|**Double**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time<br /><br /> Classified|  
|**Date**|Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered|  
  
> [!NOTE]  
>  The Time and Sequence content types are only supported by third-party algorithms. The Cyclical and Ordered content types are supported, but most algorithms treat them as discrete values and do not perform special processing.  
  
 The table also shows the *content types* supported for each data type.  
  
 The content type is specific to data mining and lets you customize the way that data is processed or calculated in the mining model. For example, even if your column contains numbers, you might need to model them as discrete values. If the column contains numbers, you can also specify that they be binned, or discretized, or specify that the model handle them as continuous values. Thus, the content type can have a huge effect on the model.. For a list of all the content types, see [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md).  
  
> [!NOTE]  
>  In other machine learning systems, you might encounter the terms *nominal data*, *factors* or *categories*, *ordinal data*, or *sequence data*. In general, these correspond to content types. In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the data type specifies only the value type for storage, not its usage in the model.  
  
## Specifying a Data Type  
 If you create the mining model directly by using Data Mining Extensions (DMX), you can define the data type for each column as you define the model, and Analysis Services will create the corresponding mining structure with the specified data types at the same time. If you create the mining model or mining structure by using a wizard, Analysis Services will suggest a data type, or you can choose a data type from a list.  
  
## Changing a Data Type  
 If you change the data type of a column, you must always reprocess the mining structure and any mining models that are based on that structure. Sometimes if you change the data type, that column can no longer be used in a particular model. In that case, Analysis Services will either raise an error when you reprocess the model, or will process the model but leave out that particular column.  
  
## See Also  
 [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md)   
 [Content Types (DMX)](assetId:///ab9dd887-df8d-4878-96b0-635881892573)   
 [Data Mining Algorithms (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md)   
 [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md)   
 [Data Types (DMX)](assetId:///4d81fe82-b187-4f80-b8ea-fe37423123a6)   
 [Mining Model Columns](../../Topics/TopicNameNotContainA/Mining-Model-Columns.md)   
 [Mining Structure Columns](../../Topics/TopicNameNotContainA/Mining-Structure-Columns.md)