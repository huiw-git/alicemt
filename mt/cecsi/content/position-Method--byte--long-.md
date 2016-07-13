---
title: position Method (byte, long)
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
  - SQLServerBlob.position (byte[], long)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
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
# position Method (byte, long)
  Returns the position of a specified pattern in the BLOB based on the given **byte** array pattern and starting index.  
  
## Syntax  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### Parameters  
 *bPattern*  
  
 The pattern to search for.  
  
 *start*  
  
 The start index to search at.  
  
## Return Value  
 A **long** value of the position where the pattern was found, or \-1 if it was not found.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This position method is specified by the position method in the java.sql.Blob interface.  
  
## See Also  
 [position Method &#40;SQLServerBlob&#41;](../content/position-Method--SQLServerBlob-.md)   
 [SQLServerBlob Methods](../content/SQLServerBlob-Methods.md)   
 [SQLServerBlob Members](../content/SQLServerBlob-Members.md)   
 [SQLServerBlob Class](../content/SQLServerBlob-Class.md)  
  
  