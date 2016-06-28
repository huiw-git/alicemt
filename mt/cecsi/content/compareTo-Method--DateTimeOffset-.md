---
title: compareTo Method (DateTimeOffset)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# compareTo Method (DateTimeOffset)
  Compares this **DateTimeOffset** object to another **DateTimeOffset** object based on the time at GMT.  
  
## Syntax  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### Parameters  
 A [DateTimeOffset](../content/DateTimeOffset-Class.md) value that you want to compare to the current instance.  
  
## Return Value  
 The following table describes the return value of this method:  
  
|Return value|Description|  
|------------------|-----------------|  
|0|Both **DateTimeOffset** objects represent the same point in time.|  
|negative number|This **DateTimeOffset** object represents a point in time that is before *other*.|  
|positive number|This **DateTimeOffset** object represents a point in time that is after *other*.|  
  
## Remarks  
 When two **DateTimeOffset** objects have the same time at GMT, there is no additional ordering of the objects based on the offset.  
  
## See Also  
 [DateTimeOffset Class](../content/DateTimeOffset-Class.md)   
 [DateTimeOffset Members](../content/DateTimeOffset-Members.md)  
  
  