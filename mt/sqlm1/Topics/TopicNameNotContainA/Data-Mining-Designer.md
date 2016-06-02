---
title: Data Mining Designer
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
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
---
# Data Mining Designer
  Data Mining Designer is the primary environment in which you work with mining models in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. You can access the designer either by selecting an existing mining structure, or by using the Data Mining Wizard to create a new mining structure and mining model. You can use Data Mining Designer to perform the following tasks:  
  
-   Modify the mining structure and the mining model that were initially created by the Data Mining Wizard.  
  
-   Create new models based on an existing mining structure.  
  
-   Train and browse mining models.  
  
-   Compare models by using accuracy charts.  
  
-   Create prediction queries based on mining models.  
  
## Mining Structure Tab  
 Use the **Mining Structure** tab to add columns and modify the properties of an existing mining structure. The following tasks and topics provide more information about working with mining structures:  
  
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
 [Mining Structure Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Structure-Tasks-and-How-tos.md)  
  
## Mining Models Tab  
 Use the **Mining Models** tab to manage existing mining models and to create new models. Mining models are always based on an existing mining structure .  
  
 In the **Mining Models** tab, you can change the algorithm type, add or remove columns that are associated with the model structure, adjust algorithm\-specific column properties, specify the mining model column usage, and adjust algorithm parameters that are associated with the mining model. You can also process the mining structure together with selected models or with all the associated models.  
  
 See the following topics for more information about working with mining models:  
  
 [Mining Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
 [Mining Model Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)  
  
## Mining Model Viewer Tab  
 Use the **Mining Model Viewer** tab to visually explore your mining models. Each mining model is associated with a custom viewer that displays content that is specific to that model. You can also view mining model content by using the content viewer.  
  
 See the following topics for more information about exploring mining models with the data mining viewers:  
  
 [Data Mining Model Viewers](../../Topics\TopicNameNotContainA/Data-Mining-Model-Viewers.md)  
  
 [Mining Model Viewer Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Viewer-Tasks-and-How-tos.md)  
  
## Mining Accuracy Chart Tab  
 Use the **Mining Accuracy Chart** tab to test the predictive accuracy of a single mining model, or to compare the effectiveness of multiple mining models contained within a mining structure. The tab contains tools for filtering the data, selecting mining models, and displaying the results in a lift chart, profit chart, or classification matrix.  
  
 See the following topics for more information about testing and validating mining models:  
  
 [Testing and Validation &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20\(Data%20Mining\).md)  
  
 [Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20Tasks%20and%20How-tos%20\(Data%20Mining\).md)  
  
## Mining Model Prediction Tab  
 The **Mining Model Prediction** tab includes Prediction Query Builder, which you can use to create a Data Mining Extensions \(DMX\) prediction query. The tab contains tools for specifying mining models and input tables, mapping the columns in the mining model to columns in the input table, adding functions to a query, and specifying criteria for each column.  
  
 After you design a query, you can use different views in the tab to display the results of the query and to modify the query manually. You can also save the results of the query to a table in a database.  
  
 See the following topics for more information about creating data mining queries:  
  
 [Data Mining Queries](../../Topics\TopicNameNotContainA/Data-Mining-Queries.md)  
  
 [Data Mining Query Tasks and How-tos](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tasks-and-How-tos.md)  
  
## See Also  
 [Data Mining Solutions](../../Topics\TopicNameNotContainA/Data-Mining-Solutions.md)  
  
  