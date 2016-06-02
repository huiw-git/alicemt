---
title: Database Element for Server (DTA)
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
|Parent element|[Server Element &#40;DTA&#41;](../Topic/Server%20Element%20\(DTA\).md)|  
|Child elements|[Name Element for Database &#40;DTA&#41;](../Topic/Name%20Element%20for%20Database%20\(DTA\).md)<br /><br /> [Schema Element for Database &#40;DTA&#41;](../Topic/Schema%20Element%20for%20Database%20\(DTA\).md)|  
  
## Remarks  
 This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Configuration** element. For more information, see [Database Element for Configuration &#40;DTA&#41;](../Topic/Database%20Element%20for%20Configuration%20\(DTA\).md).  
  
## Example  
 For a usage example of the **Database** element, see [Server Element &#40;DTA&#41;](../Topic/Server%20Element%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  