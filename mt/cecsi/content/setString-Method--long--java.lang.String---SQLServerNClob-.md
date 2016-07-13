---
title: setString Method (long, java.lang.String) (SQLServerNClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
manager:jhubbard
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
# setString Method (long, java.lang.String) (SQLServerNClob)
  Writes the specified **String** to the **NCLOB** starting at the specified position.  
  
## Syntax  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the **NCLOB**; the first position is 1.  
  
 *str*  
  
 The String to be written to the **NCLOB**.  
  
## Return Value  
 The number of characters written.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setString method is specified by the setString method in the java.sql.NClob interface.  
  
## See Also  
 [SQLServerNClob Methods](../content/SQLServerNClob-Methods.md)   
 [SQLServerNClob Members](../content/SQLServerNClob-Members.md)   
 [SQLServerNClob Class](../content/SQLServerNClob-Class.md)  
  
  