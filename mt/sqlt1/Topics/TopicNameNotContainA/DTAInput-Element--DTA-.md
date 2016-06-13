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
|**Parent element**|[DTAXML Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/DTAXML-Element--DTA-.md)|  
|**Child elements**|[Server Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)<br /><br /> [Workload Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)<br /><br /> [TuningOptions Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)<br /><br /> [Configuration Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Configuration-Element--DTA-.md)|  
  
## Remarks  
 This element is the root of the Database Engine Tuning Advisor input schema hierarchy. Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user\-specified configuration.  
  
## Example  
 For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Simple-XML-Input-File-Sample--DTA-.md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)  
  
  