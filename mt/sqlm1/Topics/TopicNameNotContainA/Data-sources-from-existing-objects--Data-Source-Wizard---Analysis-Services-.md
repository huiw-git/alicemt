---
title: Data sources from existing objects (Data Source Wizard) (Analysis Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
---
# Data sources from existing objects (Data Source Wizard) (Analysis Services)
  Use the **Data sources from existing objects** page to specify an existing data source or project on which to base the new data source.  
  
## Options  
 **Create a data source based on an existing data source in your solution**  
 Select to base the new data source on an existing data source in the solution. When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires the settings from the data source you specify when you select this option.  
  
 **Data source**  
 Select a data source on which you want to base the new data source from the list of data sources, which is grouped by project.  
  
 **Create a data source based on an Analysis Services project**  
 Select to create a new data source that references another [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project in the current solution. The new data source acquires settings from the **TargetServer** and **TargetDatabase** properties of the selected project. When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires settings from the data source you specify when you select this option.  
  
 **Project**  
 Select the project that you want to reference in the new data source.  
  
## See Also  
 [Data Source Wizard F1 Help &#40;Analysis Services&#41;](../Topic/Data%20Source%20Wizard%20F1%20Help%20\(Analysis%20Services\).md)   
 [Data Sources in Multidimensional Models](../../Topics\TopicNameNotContainA/Data-Sources-in-Multidimensional-Models.md)   
 [Supported Data Sources &#40;SSAS - Multidimensional&#41;](../Topic/Supported%20Data%20Sources%20\(SSAS%20-%20Multidimensional\).md)  
  
  