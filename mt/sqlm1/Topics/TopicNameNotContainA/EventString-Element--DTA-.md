---
title: EventString Element (DTA)
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
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
---
# EventString Element (DTA)
  Specifies a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] script workload directly in the XML input file.  
  
## Syntax  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## Element Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|**Weight**|Optional. Specifies the query weight factor \(a factor of importance\) for the specified event. Use a **float** data type to specify the weight. For example, **Weight**\="100.01". The minimum value you can specify for **Weight** is "0".|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, length is unlimited.|  
|**Default value**|None.|  
|**Occurrence**|Required once if no other type of workload is specified. You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used. For example, if you specify a workload with the **EventString** element, then you cannot also specify a workload with the **File** element in the same XML input file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Workload Element &#40;DTA&#41;](../Topic/Workload%20Element%20\(DTA\).md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](../Topic/XML%20Input%20File%20Sample%20with%20Inline%20Workload%20\(DTA\).md) .  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  