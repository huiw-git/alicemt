---
title: "Name Element for Index (DTA)"
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
ms.assetid: 2300e9cf-f0a8-49e6-b1f5-45ffe03ccb5f
caps.latest.revision: 14
manager: jhubbard
---
# Name Element for Index (DTA)
Specifies a name for an index in the user-specified configuration.  
  
## Syntax  
  
```  
  
<Create>  
    <Index>  
        <Name>...</Name>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, unlimited length.|  
|**Default value**|None.|  
|**Occurrence**|Required once for each **Index** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Index Element (DTA)](../../Topics/TopicNameNotContainA/Index-Element--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)