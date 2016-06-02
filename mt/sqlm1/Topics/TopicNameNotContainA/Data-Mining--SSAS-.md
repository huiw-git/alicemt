---
title: Data Mining (SSAS)
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
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
---
# Data Mining (SSAS)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has been a leader in predictive analytics since the 2000 release, by providing data mining in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. The combination of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining provides an integrated platform for predictive analytics that encompasses data cleansing and preparation, machine learning, and reporting. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining includes multiple standard algorithms, including EM and K\-means clustering models, neural networks, logistic regression and linear regression, decision trees, and naive bayes classifiers. All models have integrated visualizations to help you develop, refine, and evaluate your models.  Integrating data mining into business intelligence solution helps you make intelligent decisions about complex problems.  
  
## Benefits of Data Mining  
 Data mining \(also called predictive analytics and machine learning\) uses well\-researched statistical principles to discover patterns in your data. By applying the data mining algorithms in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] to your data, you can forecast trends, identify patterns, create rules and recommendations, analyze the sequence of events in complex data sets, and gain new insights.  
  
 In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], data mining is powerful, accessible, and integrated with the tools that many people prefer to use for analysis and reporting.  
  
## Key Data Mining Features  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining provides the following features in support of integrated data mining solutions:  
  
-   Multiple data sources: You can use any tabular data source for data mining, including spreadsheets and text files. You can also easily mine OLAP cubes created in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. However, you cannot use data from an in\-memory database.  
  
-   Integrated data cleansing, data management, and reporting: [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides tools for profiling and cleansing data. You can build ETL processes for cleaning data in preparation for modeling, and ssISnoversion also makes it easy to retrain and update models.  
  
-   Multiple customizable algorithms: In addition to providing algorithms such as clustering, neural networks, and decisions trees, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining supports development of your own custom plug\-in algorithms.  
  
-   Model testing infrastructure: Test your models and data sets using important statistical tools as cross\-validation, classification matrices, lift charts, and scatter plots. Easily create and manage testing and training sets.  
  
-   Querying and drillthrough: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining provides the DMX language for integrating  prediction queries into applications. You can also retrieve detailed statistics and patterns from the models, and drill through to case data.  
  
-   Client tools: In addition to the development and design studios provided by SQL Server, you can use the Data Mining Add\-ins for Excel to create, query, and browse models. Or, create custom clients, including Web services.  
  
-   Scripting language support and managed API: All data mining objects are fully programmable. Scripting is possible through MDX, XMLA, or the PowerShell extensions for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. Use the Data Mining Extensions \(DMX\) language for fast querying and scripting.  
  
-   Security and deployment: Provides role\-based security through [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], including separate permissions for drillthrough to model and structure data. Easy deployment of models to other servers, so that users can access the patterns or perform predictions  
  
## In This Section  
 The topics in this section introduce the principal features of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Data Mining and related tasks.  
  
-   [Data Mining Concepts](../../Topics\TopicNameNotContainA/Data-Mining-Concepts.md)  
  
-   [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [Mining Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
-   [Testing and Validation &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20\(Data%20Mining\).md)  
  
-   [Data Mining Queries](../../Topics\TopicNameNotContainA/Data-Mining-Queries.md)  
  
-   [Data Mining Solutions](../../Topics\TopicNameNotContainA/Data-Mining-Solutions.md)  
  
-   [Data Mining Tools](../../Topics\TopicNameNotContainA/Data-Mining-Tools.md)  
  
-   [Data Mining Architecture](../../Topics\TopicNameNotContainA/Data-Mining-Architecture.md)  
  
-   [Security Overview &#40;Data Mining&#41;](../Topic/Security%20Overview%20\(Data%20Mining\).md)  
  
## See Also  
 [SQL Server R Services](../../Topics\TopicNameNotContainA/SQL-Server-R-Services.md)  
  
  