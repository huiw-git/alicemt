---
title: "Filegroup Element for Index (DTA)"
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
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Filegroup Element for Index (DTA)
Specifies the filegroup on which the index is to be created for a user-specified configuration.  
  
## Syntax  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|**string**, unlimited length.|  
|**Default value**|None.|  
|**Occurrence**|Optional. Can use once for each **Index** element. This element cannot be used if the **PartitionScheme** and **PartitionColumn** elements are specified for the **Index** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Index Element (DTA)](../../Topics/TopicNameNotContainA/Index-Element--DTA-.md)|  
|**Child elements**|None.|  
  
## Example  
 For a usage example of this element, see [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md).  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)