---
title: "Name Element for Table (DTA)"
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Name Element for Table (DTA)
Specifies a table name for tuning.  
  
## Syntax  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, between 1 and 255 characters.|  
|**Default value**|None.|  
|**Occurrence**|Required. Once for each **Table** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Table Element for Schema (DTA)](../../Topics/TopicNameNotContainA/Table-Element-for-Schema--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example, see [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)