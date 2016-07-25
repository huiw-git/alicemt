---
title: "toString Method (DateTimeOffset)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: 8
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
# toString Method (DateTimeOffset)
  Returns a string representation of the **DateTimeOffset** object.  
  
## Syntax  
  
```  
  
public String toString()  
```  
  
## Return Value  
 A string representation of the **DateTimeOffset** object.  
  
## Remarks  
 The string has the format *YYYY*-*MM*-*DD**hh*:*mm*:*ss*[.*fffffff*] [+|-]*hh*:*mm*.  
  
 The fractional seconds of the returned string are zero padded to the declared precision. For example, a **datetimeoffset(6)** with a value of "2010-03-10 12:34:56.78 -08:00" will be formatted by DateTimeOffset.toString as "2010-03-10 12:34:56.780000 -08:00".  
  
## See Also  
 [DateTimeOffset Class](../content/DateTimeOffset-Class.md)   
 [DateTimeOffset Members](../content/DateTimeOffset-Members.md)  
  
  