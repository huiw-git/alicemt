---
title: "Configure Measure Properties"
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
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
caps.latest.revision: 51
caps.handback.revision: 0
manager: mblythe
---
# Configure Measure Properties
Measures have properties that enable you to define how the measures function and to control how the measures appear to users.  
  
 You can set properties in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] when creating or editing a cube or measure. You can also set them programmatically, using MDX or AMO. See [Create Measures and Measure Groups in Multidimensional Models](../../Topics/TopicNameNotContainA/Create-Measures-and-Measure-Groups-in-Multidimensional-Models.md) or [CREATE MEMBER Statement (MDX)](assetId:///49379217-be2c-4139-a206-1168078b9b76) or [Programming AMO OLAP basic objects](assetId:///ad1c970e-c0cb-4687-9563-56ab62c2db5f) for details.  
  
## Measure Properties  
 Measures inherit certain properties from the measure group of which they are a member, unless those properties are overridden at the measure level. Measure properties determine how a measure is aggregated, its data type, the name that is displayed to the user, the display folder in which the measure will appear, its format string, any measure expression, the underlying source column, and its visibility to users.  
  
|Property|Definition|  
|--------------|----------------|  
|**AggregateFunction**|Required. Determines how measures are aggregated. **Sum** is the default aggregation. For more information, see [Use Aggregate Functions](../../Topics/TopicNameNotContainA/Use-Aggregate-Functions.md) for a description of each function.|  
|**DataType**|Required. Specifies the data type of the column in the underlying fact table to which the measure is bound. This value is inherited from the source column by default.|  
|**Description**|Provides a description of the measure, which may be exposed in client applications.|  
|**DisplayFolder**|Specifies the folder in which the measure will appear when users connect to the cube. When a cube has many measures, you can use display folders to categorize the measures and improve the user browsing experience.|  
|**FormatString**|You can select the format that is used to display measure values to users by using the **FormatString** property of the measure.<br /><br /> Although a list of display formats is provided in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], you can specify many additional formats that are not in the list. You can specify any named or user-defined format that is valid in Microsoft Visual Basic.|  
|**ID**|Required. Displays the unique identifier (ID) of the measure. This property is read-only.|  
|**MeasureExpression**|Specifies a constrained MDX expression defining the value of the measure. The expression is evaluated at the leaf level before being aggregated, and allows for weighting of a value. For example, in currency conversion where a sales amount is weighted by the exchange rate.|  
|**Name**|Required. Specifies the name of the measure.|  
|**Source**|Required. Specifies the column in the data source view to which the measure is bound. See [Data Sources and Bindings (SSAS Multidimensional)](../../Topics/TopicNameNotContainA/Data-Sources-and-Bindings--SSAS-Multidimensional-.md).|  
|**Visible**|Determines the visibility of the measure in client applications.|  
  
## See Also  
 [Configure Measure Group Properties](../../Topics/TopicNameNotContainA/Configure-Measure-Group-Properties.md)   
 [Modifying Measures (Analysis Services Tutorial)](assetId:///7bd48810-15ce-45ff-862b-372d08606995)