---
title: "Processing Data Mining Objects"
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
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
caps.latest.revision: 21
manager: paulettm
---
# Processing Data Mining Objects
A data mining object is only an empty container until it has been processed. *Processing* a data mining model is also called *training*.  
  
 **Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data. This data is read in full and then analyzed to extract various statistics. Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache. You can either keep this cache or delete it after your models have been processed. By default, the cache is stored. For more information, see [Process a Mining Structure](../../Topics/TopicNameContainA/Process-a-Mining-Structure.md).  
  
 **Processing mining models:** A mining model is empty, containing definitions only, until it is processed. To process a mining model, the mining structure that it is based on must have been processed. The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns. After the model is processed, the model stores only the results of processing, not the data itself. For more information, see [Process a Mining Model](../../Topics/TopicNameContainA/Process-a-Mining-Model.md).  
  
 The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.  
  
 ![Processing of data: source to structure to model](../../Topics/TopicNameNotContainA/images/dmcon_ModelArch.gif "dmcon_ModelArch")  
  
## Viewing the Results of Processing  
 After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis. If the cache has not been cleared, you can access the data in this cache in the following ways:  
  
-   Creating a Data Mining Extensions (DMX) query on the model and drilling through to the structure. For more information, see [SELECT FROM <model\>.CASES (DMX)](assetId:///d58acb47-aaa6-40b7-b8c4-6a6700fbc1dd).  
  
-   Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases. For more information, see [Data Mining Model Viewers](../../Topics/TopicNameNotContainA/Data-Mining-Model-Viewers.md), or [Drill Through to Case Data from a Mining Model](../../Topics/TopicNameContainA/Drill-Through-to-Case-Data-from-a-Mining-Model.md).  
  
-   Creating a DMX query on the structure cases. For more information, see [SELECT FROM <structure\>.CASES](assetId:///36f50213-14dc-42da-b899-20240b781e1a).  
  
 After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data. You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.  
  
 The model content for each mining model depends on the algorithm that was used to create it. For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data. For more information, see [Mining Model Content (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content--Analysis-Services---Data-Mining-.md).  
  
## Processing Requirements  
 Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.  
  
 For relational data source, processing requires only that you create training data and run mining algorithms on that data. However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state. This may requires that the multidimensional objects be processed to populate the mining model.  
  
 For more information, see [Processing Requirements and Considerations (Data Mining)](../../Topics/TopicNameNotContainA/Processing-Requirements-and-Considerations--Data-Mining-.md).  
  
## See Also  
 [Drillthrough Queries (Data Mining)](../../Topics/TopicNameNotContainA/Drillthrough-Queries--Data-Mining-.md)   
 [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md)   
 [Mining Models (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Models--Analysis-Services---Data-Mining-.md)   
 [Logical Architecture (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Logical-Architecture--Analysis-Services---Data-Mining-.md)