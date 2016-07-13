---
title: getSubString Method (SQLServerClob)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerClob.getSubString
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
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
# getSubString Method (SQLServerClob)
  Returns a copy of the specified substring in the CLOB based on the given starting position and the number of characters to copy.  
  
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
 A **String** that is the specified substring in the CLOB.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSubString method is specified by the getSubString method in the java.sql.Clob interface.  
  
 Trying to get zero characters from a null or zero\-length CLOB returns an empty string. Trying to get any length of characters at any position other than position 1 in a zero\-length CLOB will cause a position exception to be thrown.  
  
## See Also  
 [SQLServerClob Methods](../content/SQLServerClob-Methods.md)   
 [SQLServerClob Members](../content/SQLServerClob-Members.md)   
 [SQLServerClob Class](../content/SQLServerClob-Class.md)  
  
  