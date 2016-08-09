---
title: "Table Element for Schema (DTA)"
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
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Table Element for Schema (DTA)
Specifies the table for tuning.  
  
## Syntax  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## Element Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|**NumberOfRows**|Optional. Integer that allows you to simulate tables of different sizes.|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, between 1 and 255 characters.|  
|**Default value**|None.|  
|**Occurrence**|Optional. List as many tables as appropriate for your workload.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Schema Element for Database (DTA)](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)|  
|**Child elements**|[Name Element for Table (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Table--DTA-.md)|  
  
## Remarks  
 If you do not specify a **Table** element, Database Engine Tuning Advisor will assume all tables on the specified database can be tuned.  
  
## Example  
 For a usage example, see [Server Element (DTA)](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)