---
title: "Database Element for Configuration (DTA)"
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
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Database Element for Configuration (DTA)
Specifies the database against which you want the Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the **Configuration** element).  
  
## Syntax  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required one or more times per **Server** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Server Element for Configuration (DTA)](../../Topics/TopicNameNotContainA/Server-Element-for-Configuration--DTA-.md)|  
|**Child elements**|[Name Element for Database (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Database--DTA-.md)<br /><br /> [Schema Element for Database (DTA)](../../Topics/TopicNameNotContainA/Schema-Element-for-Database--DTA-.md)<br /><br /> [Recommendation Element (DTA)](../../Topics/TopicNameNotContainA/Recommendation-Element--DTA-.md)|  
  
## Remarks  
 This element is of the **DatabaseTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Server** element, which occurs at the top of the XML input file. For more information, see [Database Element for Server (DTA)](../../Topics/TopicNameNotContainA/Database-Element-for-Server--DTA-.md).  
  
## Example  
 For a usage example of this **Database** element, see the [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)