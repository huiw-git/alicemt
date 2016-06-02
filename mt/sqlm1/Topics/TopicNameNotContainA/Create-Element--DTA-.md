---
title: Create Element (DTA)
ms.custom: na
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
---
# Create Element (DTA)
  Contains information about the indexes, statistics, or heap structures in a user\-specified configuration.  
  
## Syntax  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once for each physical design structure type \(indexes, statistics, or heap structures\).|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Recommendation Element &#40;DTA&#41;](../Topic/Recommendation%20Element%20\(DTA\).md)|  
|**Child elements**|[Index Element &#40;DTA&#41;](../Topic/Index%20Element%20\(DTA\).md)<br /><br /> **Statistics** Element \(see [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) for information\)<br /><br /> **Heap** Element \(see [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) for information\)|  
  
## Remarks  
 This element is of the **CreateTypecomplexType** name in the Database Engine Tuning Advisor XML schema. It is used to create indexes, statistics, and heap structures for a user\-specified configuration. Do not confuse this **Create** element with the other types that can be used to create views \(**CreateViewType**\) or partitioning \(**CreatePType**\). Refer to the [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) for information about these other **Create** element types.  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](../Topic/XML%20Input%20File%20Sample%20with%20User-specified%20Configuration%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  