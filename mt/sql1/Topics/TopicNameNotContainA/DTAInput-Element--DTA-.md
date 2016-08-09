---
title: "DTAInput Element (DTA)"
ms.custom: na
ms.date: 06/29/2016
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
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
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
|**Parent element**|[DTAXML Element (DTA)](../../Topics/TopicNameNotContainA/DTAXML-Element--DTA-.md)|  
|**Child elements**|[Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)<br /><br /> [Workload Element (DTA)](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)<br /><br /> [TuningOptions Element (DTA)](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)<br /><br /> [Configuration Element (DTA)](../../Topics/TopicNameNotContainA/Configuration-Element--DTA-.md)|  
  
## Remarks  
 This element is the root of the Database Engine Tuning Advisor input schema hierarchy. Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user-specified configuration.  
  
## Example  
 For a usage example of the **DTAInput** element, see [Simple XML Input File Sample (DTA)](../../Topics/TopicNameNotContainA/Simple-XML-Input-File-Sample--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)