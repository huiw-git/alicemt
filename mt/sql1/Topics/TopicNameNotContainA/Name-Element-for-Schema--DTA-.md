---
title: "Name Element for Schema (DTA)"
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
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
caps.latest.revision: 14
manager: jhubbard
---
# Name Element for Schema (DTA)
Contains name of the schema.  
  
## Syntax  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, between 1 and 255 characters|  
|**Default value**|None.|  
|**Occurrence**|Required once per **Schema** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Schema Element for Database (DTA)](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)