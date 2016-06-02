---
title: Data Mining Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
---
# Data Mining Properties
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports the data mining server properties listed in the following tables. For more information about additional server properties and how to set them, see [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md).  
  
 **Applies to:** Multidimensional server mode only  
  
## Non\-Specific Category  
 **AllowSessionMiningModels**  
 A Boolean property that indicates whether session mining models can be created.  
  
 The default value for this property is false, which indicates that session mining models cannot be created.  
  
 **AllowAdHocOpenRowsetQueries**  
 A Boolean property that indicates whether adhoc open rowset queries are allowed.  
  
 The default value for this property is false, which indicates that open rowset queries are not allowed during a session.  
  
 **AllowedProvidersInOpenRowset**  
 A string property that identifies which providers are allowed in an open rowset, consisting of a comma\/semi\-colon separated list of provider ProgIDs, or else \[All\].  
  
 **MaxConcurrentPredictionQueries**  
 A signed 32\-bit integer property that defines the maximum number of concurrent prediction queries.  
  
## Algorithms Category  
 **Microsoft\_Association\_Rules\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Association\_Rules algorithm is enabled.  
  
 **Microsoft\_Clustering\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Clustering algorithm is enabled.  
  
 **Microsoft\_Decision\_Trees\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_DecisionTrees algorithm is enabled.  
  
 **Microsoft\_Naive\_Bayes\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_ Naive\_Bayes algorithm is enabled.  
  
 **Microsoft\_Neural\_Network\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Neural\_Network algorithm is enabled.  
  
 **Microsoft\_Sequence\_Clustering\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Sequence\_Clustering algorithm is enabled.  
  
 **Microsoft\_Time\_Series\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Time\_Series algorithm is enabled.  
  
 **Microsoft\_Linear\_Regression\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Linear\_Regression algorithm is enabled.  
  
 **Microsoft\_Logistic\_Regression\\ Enabled**  
 A Boolean property that indicates whether the Microsoft\_Logistic\_Regression algorithm is enabled.  
  
> [!NOTE]  
>  In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms. You configure these properties when you create an individual data mining model, not at the server level. For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
## See Also  
 [Physical Architecture &#40;Analysis Services - Data Mining&#41;](../Topic/Physical%20Architecture%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)  
  
  