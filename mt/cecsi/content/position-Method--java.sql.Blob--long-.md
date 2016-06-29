---
title: position Method (java.sql.Blob, long)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerBlob.position (java.sql.Blob.long)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ebd005e5-f6c5-4789-87f9-d2fdacd35060
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
# position Method (java.sql.Blob, long)
  Returns the position of a specified pattern in the BLOB based on the given pattern and starting index.  
  
## Syntax  
  
```  
  
public long position(java.sql.Blob pattern,  
                     long start)  
```  
  
#### Parameters  
 *pattern*  
  
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
  
  