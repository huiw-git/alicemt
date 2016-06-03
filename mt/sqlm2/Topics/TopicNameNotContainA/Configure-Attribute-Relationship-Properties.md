---
title: Configure Attribute Relationship Properties
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
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
---
# Configure Attribute Relationship Properties
  The following table lists and describes the properties of an attribute relationship.  
  
|Property|Description|  
|--------------|-----------------|  
|Attribute|Contains the name of the attribute.|  
|Cardinality|Indicates the cardinality of the relationship. Values are Many, for a many to one relationship, or One, for a one to one relationship. Default value is Many. In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], the cardinality property has no effect \- its use is reserved for a future implementation.|  
|Name|Contains the friendly name of the attribute.|  
|RelationshipType|Indicates whether member relationships change over time. Values are Rigid, which means that relationships between members do not change over time, or Flexible, which means that relationships between members change over time. Default is Flexible. If you define a relationship as flexible, aggregations are dropped and recomputed as part of an incremental update \(they will not be dropped if only new members are added\). If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] retains aggregations when the dimension is incrementally updated. If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] generates an error during incremental processing. Specifying the appropriate relationships and relationship properties increases query and processing performance.|  
|Visible|Determines the visibility of the attribute relationship. Values are True or False. Default is True.|  
  
  