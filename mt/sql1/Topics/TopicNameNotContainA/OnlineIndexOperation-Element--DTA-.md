---
title: "OnlineIndexOperation Element (DTA)"
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
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
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
|**Allowed values**|**OFF**<br /> No recommended physical design structures can be created online.<br /><br /> **ON**<br /> All recommended physical design structures can be created online.<br /><br /> **MIXED**<br /> Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.<br /><br /> Use one of these values with this element. If indexes are created online, the keyword **ONLINE = ON** is appended to its object definition.|  
|**Default value**|None.|  
|**Occurrence**|Optional. If used, can only be used once for the **TuningOptions** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[TuningOptions Element (DTA)](../../Topics/TopicNameNotContainA/TuningOptions-Element--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see the [Simple XML Input File Sample (DTA)](../../Topics/TopicNameNotContainA/Simple-XML-Input-File-Sample--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)