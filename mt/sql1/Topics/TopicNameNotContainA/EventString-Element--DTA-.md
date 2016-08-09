---
title: "EventString Element (DTA)"
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
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# EventString Element (DTA)
Specifies a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] script workload directly in the XML input file.  
  
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
|**Weight**|Optional. Specifies the query weight factor (a factor of importance) for the specified event. Use a **float** data type to specify the weight. For example, **Weight**="100.01". The minimum value you can specify for **Weight** is "0".|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, length is unlimited.|  
|**Default value**|None.|  
|**Occurrence**|Required once if no other type of workload is specified. You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used. For example, if you specify a workload with the **EventString** element, then you cannot also specify a workload with the **File** element in the same XML input file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Workload Element (DTA)](../../Topics/TopicNameNotContainA/Workload-Element--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with Inline Workload (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-Inline-Workload--DTA-.md) .  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)