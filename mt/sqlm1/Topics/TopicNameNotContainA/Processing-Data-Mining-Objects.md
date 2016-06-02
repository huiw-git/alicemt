---
title: Processing Data Mining Objects
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
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
---
# Processing Data Mining Objects
  A data mining object is only an empty container until it has been processed. *Processing* a data mining model is also called *training*.  
  
 **Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data. This data is read in full and then analyzed to extract various statistics. Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache. You can either keep this cache or delete it after your models have been processed. By default, the cache is stored. For more information, see [Process a Mining Structure](../../Topics\TopicNameContainA/Process-a-Mining-Structure.md).  
  
 **Processing mining models:** A mining model is empty, containing definitions only, until it is processed. To process a mining model, the mining structure that it is based on must have been processed. The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns. After the model is processed, the model stores only the results of processing, not the data itself. For more information, see [Process a Mining Model](../../Topics\TopicNameContainA/Process-a-Mining-Model.md).  
  
 The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.  
  
 ![Processing of data: source to structure to model](../../Images\Image\ImageNotContaina/dmcon_ModelArch.gif "dmcon_ModelArch")  
  
## Viewing the Results of Processing  
 After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis. If the cache has not been cleared, you can access the data in this cache in the following ways:  
  
-   Creating a Data Mining Extensions \(DMX\) query on the model and drilling through to the structure. For more information, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](../Topic/SELECT%20FROM%20%3Cmodel%3E.CASES%20\(DMX\).md).  
  
-   Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases. For more information, see [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md), or [Drill Through to Case Data from a Mining Model](../../Topics\TopicNameContainA/Drill-Through-to-Case-Data-from-a-Mining-Model.md).  
  
-   Creating a DMX query on the structure cases. For more information, see [SELECT FROM &#60;structure&#62;.CASES](../Topic/SELECT%20FROM%20%3Cstructure%3E.CASES.md).  
  
 After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data. You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.  
  
 The model content for each mining model depends on the algorithm that was used to create it. For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data. For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
## Processing Requirements  
 Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.  
  
 For relational data source, processing requires only that you create training data and run mining algorithms on that data. However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state. This may requires that the multidimensional objects be processed to populate the mining model.  
  
 For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../Topic/Processing%20Requirements%20and%20Considerations%20\(Data%20Mining\).md).  
  
## See Also  
 [Drillthrough Queries &#40;Data Mining&#41;](../Topic/Drillthrough%20Queries%20\(Data%20Mining\).md)   
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Logical Architecture &#40;Analysis Services - Data Mining&#41;](../Topic/Logical%20Architecture%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
  