---
title: getSubString Method (SQLServerNClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
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
# getSubString Method (SQLServerNClob)
  Retrieves a copy of the specified substring in the **NCLOB** based on the specified starting position and the number of characters to copy.  
  
## Syntax  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### Parameters  
 *pos*  
  
 The first character of the substring to be extracted. The first character is at position 1.  
  
 *length*  
  
 The number of consecutive characters to be copied.  
  
## Return Value  
 A **String** that is the specified substring in the **NCLOB**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSubString method is specified by the getSubString method in the java.sql.NClob interface.  
  
 Trying to get zero characters from a null or zero\-length NCLOB returns an empty string. Trying to get any length of characters at any position other than position 1 in a zero\-length NCLOB will cause a position exception to be thrown.  
  
## See Also  
 [SQLServerNClob Methods](../content/SQLServerNClob-Methods.md)   
 [SQLServerNClob Members](../content/SQLServerNClob-Members.md)   
 [SQLServerNClob Class](../content/SQLServerNClob-Class.md)  
  
  