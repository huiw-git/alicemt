---
title: getBinaryStream Method (long, long)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30bc8882-04b4-4efd-95e4-7d3a2a8c1d47
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
# getBinaryStream Method (long, long)
  Returns an input stream object that contains a partial BLOB value by using the specified starting position and the length.  
  
## Syntax  
  
```  
  
public java.io.InputStream getBinaryStream(long pos, long length)  
```  
  
#### Parameters  
 *pos*  
  
 The offset to the first byte of the partial value to be retrieved.  
  
 *length*  
  
 The length in bytes of the partial value to be retrieved.  
  
## Return Value  
 An input stream that contains the BLOB data.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBinaryStream method is specified by the getBinaryStream method in the java.sql.Blob interface.  
  
## See Also  
 [SQLServerBlob Methods](../content/SQLServerBlob-Methods.md)   
 [SQLServerBlob Members](../content/SQLServerBlob-Members.md)   
 [SQLServerBlob Class](../content/SQLServerBlob-Class.md)  
  
  