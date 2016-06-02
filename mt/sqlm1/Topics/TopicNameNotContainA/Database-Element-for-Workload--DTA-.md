---
title: Database Element for Workload (DTA)
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
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
---
# Database Element for Workload (DTA)
  Specifies the database where the workload trace table is located.  
  
## Syntax  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once if no other type of workload is specified. You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used. For example, if you specify a workload with the **Database** element, you cannot also specify a workload with the **File** element in the same XML input file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md)|  
|**Child elements**|[Name Element for Database &#40;DTA&#41;](../Topic/Name%20Element%20for%20Database%20\(DTA\).md)<br /><br /> [Schema Element for Database &#40;DTA&#41;](../Topic/Schema%20Element%20for%20Database%20\(DTA\).md)|  
  
## Remarks  
 This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema. Do not confuse this **Database** element with the one whose root parent is the **Configuration** element. \(See [Database Element for Configuration &#40;DTA&#41;](../Topic/Database%20Element%20for%20Configuration%20\(DTA\).md).\)  
  
## Example  
 For a usage example of this **Database** element, see the code example in [Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  