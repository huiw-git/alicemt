---
title: "position Method (java.sql.NClob, long)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: 13
manager: jhubbard
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
# position Method (java.sql.NClob, long)
  Retrieves the character position at which the specified **NClob** object *searchstr* appears in this **NClob** object.  
  
## Syntax  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### Parameters  
 *searchstr*  
  
 A NClob object for which to search.  
  
 *start*  
  
 The position at which to begin searching; the first position is 1.  
  
## Return Value  
 The position at which the substring appears, or -1 if it is not present. The first position is 1.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This position method is specified by the position method in the java.sql.NClob interface.  
  
## See Also  
 [position Method &#40;SQLServerNClob&#41;](../content/position-Method--SQLServerNClob-.md)   
 [SQLServerNClob Methods](../content/SQLServerNClob-Methods.md)   
 [SQLServerNClob Members](../content/SQLServerNClob-Members.md)   
 [SQLServerNClob Class](../content/SQLServerNClob-Class.md)  
  
  