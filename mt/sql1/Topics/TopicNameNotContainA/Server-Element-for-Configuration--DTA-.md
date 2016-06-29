---
title: Server Element for Configuration (DTA)
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
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
---
# Server Element for Configuration (DTA)
  Contains the identifying information for the server where you want Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the **Configuration** element).  
  
## Syntax  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once per **Configuration** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Configuration Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Configuration-Element--DTA-.md)|  
|**Child elements**|[Name Element for Server &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Name-Element-for-Server--DTA-.md)<br /><br /> [Database Element for Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Database-Element-for-Configuration--DTA-.md)|  
  
## Remarks  
 You can specify only one **Server** element for the **Configuration** element. This element is of the **ServerTypecomplexType** name in the [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100). Do not confuse this **Server** element with the one that is the child of the **DTAInput** element. For more information, see [Server Element &#40;DTA&#41;](../../Topics/TopicNameNotContainA/Server-Element--DTA-.md).  
  
## Example  
 For a usage example, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)  
  
  