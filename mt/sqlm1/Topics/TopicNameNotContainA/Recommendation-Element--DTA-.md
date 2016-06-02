---
title: Recommendation Element (DTA)
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
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
---
# Recommendation Element (DTA)
  Contains information about the hypothetical indexes that are part of a user\-specified configuration.  
  
## Syntax  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Optional. Can use once for each **Table** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Table Element for Schema &#40;DTA&#41;](../Topic/Table%20Element%20for%20Schema%20\(DTA\).md)|  
|**Child elements**|[Create Element &#40;DTA&#41;](../Topic/Create%20Element%20\(DTA\).md)<br /><br /> **Drop** element. For more information, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## Remarks  
 This element is of the **RecommendationTypecomplexType** name in the Database Engine Tuning Advisor XML schema. It is used to specify indexes for a hypothetical configuration. Do not confuse this **Recommendation** element with the other types that can be used to specify partitioning \(**RecommendationPType**\) or views \(**RecommendationViewType**\). For information about these other **Recommendation** element types, see the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](../Topic/XML%20Input%20File%20Sample%20with%20User-specified%20Configuration%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  