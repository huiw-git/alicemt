---
title: DTAInput Element (DTA)
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
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
---
# DTAInput Element (DTA)
  Contains the definition of XML input for Database Engine Tuning Advisor.  
  
## Syntax  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## Element Characteristics  
  
|Characteristics|Description|  
|---------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Optional once per **DTAXML** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[DTAXML Element &#40;DTA&#41;](../Topic/DTAXML%20Element%20\(DTA\).md)|  
|**Child elements**|[Server Element &#40;DTA&#41;](../Topic/Server%20Element%20\(DTA\).md)<br /><br /> [Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md)<br /><br /> [TuningOptions Element &#40;DTA&#41;](../Topic/TuningOptions%20Element%20\(DTA\).md)<br /><br /> [Configuration Element &#40;DTA&#41;](../Topic/Configuration%20Element%20\(DTA\).md)|  
  
## Remarks  
 This element is the root of the Database Engine Tuning Advisor input schema hierarchy. Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user\-specified configuration.  
  
## Example  
 For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](../Topic/Simple%20XML%20Input%20File%20Sample%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  