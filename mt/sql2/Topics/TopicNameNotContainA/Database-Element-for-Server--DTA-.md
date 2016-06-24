---
title: Database Element for Server (DTA)
H1: na
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
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
---
# Database Element for Server (DTA)
  Specifies the database you want to tune on a specific server.  
  
## Syntax  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|Data type and length|None.|  
|Default value|None.|  
|Occurrence|Required one or more times per **Server** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|Parent element|[Server Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md)|  
|Child elements|[Name Element for Database &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Database--DTA-.md)<br /><br /> [Schema Element for Database &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)|  
  
## Remarks  
 This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Configuration** element. For more information, see [Database Element for Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Configuration--DTA-.md).  
  
## Example  
 For a usage example of the **Database** element, see [Server Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)  
  
  