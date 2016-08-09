---
title: "Schema Element for Database (DTA)"
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
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# Schema Element for Database (DTA)
Specifies the schema of the database that you want to tune.  
  
## Syntax  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once for the **Database** element that is specified under the **Server** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Database Element for Server (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Server--DTA-.md)|  
|**Child elements**|[Name Element for Schema (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Schema--DTA-.md)<br /><br /> [Table Element for Schema (DTA)](../../Topics/TopicNameNotContainA/Table-Element-for-Schema--DTA-.md)|  
  
## Example  
 For a usage example of this element, see [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)