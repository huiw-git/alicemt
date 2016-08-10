---
title: "Name Element for Server (DTA)"
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
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# Name Element for Server (DTA)
Contains the name of the server where the databases you want to tune reside.  
  
## Syntax  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, between 1 and 255 characters.|  
|**Default value**|None.|  
|**Occurrence**|Required once per **Server** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For an example of how this **Name** element is used, see [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)