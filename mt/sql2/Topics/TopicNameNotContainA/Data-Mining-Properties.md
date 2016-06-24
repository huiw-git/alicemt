---
title: Data Mining Properties
H1: na
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
  [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] supports the data mining server properties listed in the following tables. For more information about additional server properties and how to set them, see [Server Properties in Analysis Services](../../Topics/TopicNameNotContainA/Server-Properties-in-Analysis-Services.md).  
  
 **Applies to:** Multidimensional server mode only  
  
## Non-Specific Category  
 **AllowSessionMiningModels**  
 A Boolean property that indicates whether session mining models can be created.  
  
 The default value for this property is false, which indicates that session mining models cannot be created.  
  
 **AllowAdHocOpenRowsetQueries**  
 A Boolean property that indicates whether adhoc open rowset queries are allowed.  
  
 The default value for this property is false, which indicates that open rowset queries are not allowed during a session.  
  
 **AllowedProvidersInOpenRowset**  
 A string property that identifies which providers are allowed in an open rowset, consisting of a comma/semi-colon separated list of provider ProgIDs, or else [All].  
  
 **MaxConcurrentPredictionQueries**  
 A signed 32-bit integer property that defines the maximum number of concurrent prediction queries.  
  
## Algorithms Category  
 **Microsoft_Association_Rules\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Association_Rules algorithm is enabled.  
  
 **Microsoft_Clustering\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Clustering algorithm is enabled.  
  
 **Microsoft_Decision_Trees\ Enabled**  
 A Boolean property that indicates whether the Microsoft_DecisionTrees algorithm is enabled.  
  
 **Microsoft_Naive_Bayes\ Enabled**  
 A Boolean property that indicates whether the Microsoft_ Naive_Bayes algorithm is enabled.  
  
 **Microsoft_Neural_Network\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Neural_Network algorithm is enabled.  
  
 **Microsoft_Sequence_Clustering\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Sequence_Clustering algorithm is enabled.  
  
 **Microsoft_Time_Series\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Time_Series algorithm is enabled.  
  
 **Microsoft_Linear_Regression\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Linear_Regression algorithm is enabled.  
  
 **Microsoft_Logistic_Regression\ Enabled**  
 A Boolean property that indicates whether the Microsoft_Logistic_Regression algorithm is enabled.  
  
> [!NOTE]  
>  In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms. You configure these properties when you create an individual data mining model, not at the server level. For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md).  
  
## See Also  
 [Physical Architecture &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Physical-Architecture--Analysis-Services---Data-Mining-.md)   
 [Server Properties in Analysis Services](../../Topics/TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Determine the Server Mode of an Analysis Services Instance](../../Topics/TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)  
  
  