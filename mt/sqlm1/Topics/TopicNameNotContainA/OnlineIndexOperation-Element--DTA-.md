---
title: OnlineIndexOperation Element (DTA)
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
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
---
# OnlineIndexOperation Element (DTA)
  Specifies whether the indexes, indexed views, or partitions that Database Engine Tuning Advisor recommends can be created online.  
  
## Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, no maximum length.|  
|**Allowed values**|**OFF**<br /> No recommended physical design structures can be created online.<br /><br /> **ON**<br /> All recommended physical design structures can be created online.<br /><br /> **MIXED**<br /> Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.<br /><br /> Use one of these values with this element. If indexes are created online, the keyword **ONLINE \= ON** is appended to its object definition.|  
|**Default value**|None.|  
|**Occurrence**|Optional. If used, can only be used once for the **TuningOptions** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[TuningOptions Element &#40;DTA&#41;](../Topic/TuningOptions%20Element%20\(DTA\).md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](../Topic/Simple%20XML%20Input%20File%20Sample%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  