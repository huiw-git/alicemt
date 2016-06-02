---
title: TestServer Element (DTA)
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
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
---
# TestServer Element (DTA)
  Specifies the test server to use when tuning a production server.  
  
## Syntax  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, unlimited length.|  
|**Default value**|None.|  
|**Occurrence**|Optional. Can use once for each **TuningOptions** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[TuningOptions Element &#40;DTA&#41;](../Topic/TuningOptions%20Element%20\(DTA\).md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [Reduce the Production Server Tuning Load](../../Topics\TopicNameNotContainA/Reduce-the-Production-Server-Tuning-Load.md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  