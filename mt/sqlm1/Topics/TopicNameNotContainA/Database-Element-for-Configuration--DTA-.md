---
title: Database Element for Configuration (DTA)
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
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
---
# Database Element for Configuration (DTA)
  Specifies the database against which you want the Database Engine Tuning Advisor to evaluate the hypothetical configuration \(specified by the **Configuration** element\).  
  
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
|**Parent element**|[Server Element for Configuration &#40;DTA&#41;](../Topic/Server%20Element%20for%20Configuration%20\(DTA\).md)|  
|**Child elements**|[Name Element for Database &#40;DTA&#41;](../Topic/Name%20Element%20for%20Database%20\(DTA\).md)<br /><br /> [Schema Element for Database &#40;DTA&#41;](../Topic/Schema%20Element%20for%20Database%20\(DTA\).md)<br /><br /> [Recommendation Element &#40;DTA&#41;](../Topic/Recommendation%20Element%20\(DTA\).md)|  
  
## Remarks  
 This element is of the **DatabaseTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Server** element, which occurs at the top of the XML input file. For more information, see [Database Element for Server &#40;DTA&#41;](../Topic/Database%20Element%20for%20Server%20\(DTA\).md).  
  
## Example  
 For a usage example of this **Database** element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](../Topic/XML%20Input%20File%20Sample%20with%20User-specified%20Configuration%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  