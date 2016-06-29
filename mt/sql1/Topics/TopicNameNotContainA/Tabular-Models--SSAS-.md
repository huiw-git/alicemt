---
title: Tabular Models (SSAS)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
---
# Tabular Models (SSAS)
  Tabular models are Analysis Services databases that run in\-memory or in DirectQuery mode, accessing data directly from backend relational data sources.  
  
 In\-memory is the default. Using state\-of\-the\-art compression algorithms and multi\-threaded query processor, the in\-memory analytics engine delivers fast access to tabular model objects and data by reporting client applications such as Microsoft Excel and Microsoft [!INCLUDE[ssCrescent](../../Topics/TopicNameContainA/includes/ssCrescent_md.md)].  
  
 DirectQuery is an alternative query mode for models that  are either too big to fit in memory, or when data volatility precludes  a reasonable processing strategy. In this release, DirectQuery achieves greater parity with in\-memory models through support for additional data sources, ability to handle calculated tables and columns in a DirectQuery model, row level security via DAX expressions that reach the backend database, and query optimizations that result in faster throughput than in previous versions. Taking advantage of recent enhancements requires compatibility level 1200, introduced in this release.  
  
 Tabular models are authored in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/includes/ssBIDevStudioFull_md.md)] using the Tabular model project template that provides a design surface for creating a model, tables, relationships, and DAX expressions. You can import data from multiple sources, and then enrich the model by adding relationships, calculated tables and columns, measures, KPIs, hierarchies, and translations.  
  
 Models can then be deployed to an instance of Analysis Services configured for Tabular server mode, where client reporting applications can connect to them. Deployed models can be managed in SQL Server Management Studio just like multidimensional models. They can also be partitioned for optimized processing and secured to the row\-level by using role based security.  
  
## In This Section  
 [Tabular Model Solutions &#40;SSAS Tabular&#41;](../../Topics/TopicNameNotContainA/Tabular-Model-Solutions--SSAS-Tabular-.md)  
  
 [Tabular Model Databases &#40;SSAS Tabular&#41;](../../Topics/TopicNameNotContainA/Tabular-Model-Databases--SSAS-Tabular-.md)  
  
 [Tabular Model Data Access](../../Topics/TopicNameNotContainA/Tabular-Model-Data-Access.md)  
  
## See Also  
 [What's New in Analysis Services](../../Topics/TopicNameNotContainA/What-s-New-in-Analysis-Services.md)   
 [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](../../Topics/TopicNameNotContainA/Comparing-Tabular-and-Multidimensional-Solutions--SSAS-.md)   
 [Tools and applications used in Analysis Services](../../Topics/TopicNameNotContainA/Tools-and-applications-used-in-Analysis-Services.md)   
 [DirectQuery Mode &#40;SSAS Tabular&#41;](../../Topics/TopicNameNotContainA/DirectQuery-Mode--SSAS-Tabular-.md)   
 [Compatibility Level for Tabular models in Analysis Services](../../Topics/TopicNameNotContainA/Compatibility-Level-for-Tabular-models-in-Analysis-Services.md)  
  
  