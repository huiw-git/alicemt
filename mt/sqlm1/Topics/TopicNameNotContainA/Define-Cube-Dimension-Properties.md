---
title: Define Cube Dimension Properties
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
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
---
# Define Cube Dimension Properties
  A cube dimension is an instance of a database dimension within a cube. A database dimension can be used in multiple cubes, and multiple cube dimensions can be based on a single database dimension. The following table describes the properties of a cube dimension.  
  
|Property|Description|  
|--------------|-----------------|  
|**AllMemberAggregationUsage**|Controls how aggregations are designed by the Aggregation Designer in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. This property can have the following values:<br /><br /> **Full**: Every aggregation for the cube must include the All member.<br /><br /> **None**: No aggregation for the cube can include the All member. This is the default value.<br /><br /> **Unrestricted**: No restrictions are placed on the Aggregation Designer.<br /><br /> **Default**: The same functionality as Unrestricted.|  
|**Description**|Provides a descriptive name for the level.|  
|**DimensionID**|Contains the unique identifier \(ID\) of the database dimension.|  
|**HierarchyUniqueNameStyle**|Determines how unique names are generated for hierarchies that are contained within the cube dimension. This property can have the following values:<br /><br /> **IncludeDimensionName**:<br />                    The name of the dimension is included as part of the name of the hierarchy. This is the default value.<br /><br /> **ExcludeDimensionName**:<br />                    The name of the dimension is not included as part of the name of the hierarchy.|  
|**ID**|Contains the unique identifier of the cube dimension.|  
|**MemberUniqueNameStyle**|Determines how unique names are generated for members of hierarchies contained within the cube dimension. This property can have the following values:<br /><br /> **Native**:<br />                      [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] automatically determines the unique names of members. This is the default value.<br /><br /> **NamePath**: [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] generates a compound name consisting of the name of each level and the caption of the member.|  
|**Name**|Contains the friendly name of the cube dimension. By default, the name of a cube dimension is the same as the name of the database dimension, unless another cube dimension of the same name is already defined.|  
|**Visible**|Determines whether the cube dimension is visible. The default value is **True**.|  
  
## See Also  
 [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Dimensions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  