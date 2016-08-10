---
title: "Name Element for Column (DTA)"
ms.custom: na
ms.date: 08/09/2016
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Name Element for Column (DTA)
Specifies the name for an index column in a user-specified configuration.  
  
## Syntax  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, unlimited length.|  
|**Default value**|None.|  
|**Occurrence**|Required once for each **Column** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Column Element for Index (DTA)](../../Topics/TopicNameNotContainA/Column-Element-for-Index--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)