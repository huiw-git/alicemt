---
title: "Configuration Element (DTA)"
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
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 17
manager: jhubbard
---
# Configuration Element (DTA)
Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.  
  
## Syntax  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## Element Attributes  
  
|Configuration Attribute|Description|  
|-----------------------------|-----------------|  
|**SpecificationMode**|Optional. Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one. Use a **string** data type to specify this attribute with one of the following allowed values:<br /><br /> **Relative**:<br />                  Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned. For example:<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  Evaluates the specified configuration as a standalone configuration. When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration. For example:<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Optional. Can use once for each **DTAInput** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[DTAInput Element (DTA)](../../Topics/TopicNameNotContainA/DTAInput-Element--DTA-.md)|  
|**Child elements**|[Server Element for Configuration (DTA)](../../Topics/TopicNameNotContainA/Server-Element-for-Configuration--DTA-.md)|  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)