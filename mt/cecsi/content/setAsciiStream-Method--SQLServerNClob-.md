---
title: setAsciiStream Method (SQLServerNClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
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
# setAsciiStream Method (SQLServerNClob)
  Retrieves a stream to be used to write ASCII characters to the **NCLOB** value that this **java.sql.NClob** object represents, starting at the specified position.  
  
## Syntax  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the **NCLOB** object; the first position is 1.  
  
## Return Value  
 An OutputStream object that represents the stream to which ASCII encoded characters can be written.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setAsciiStream method is specified by the setAsciiStream method in the java.sql.NClob interface.  
  
## See Also  
 [SQLServerNClob Methods](../content/SQLServerNClob-Methods.md)   
 [SQLServerNClob Members](../content/SQLServerNClob-Members.md)   
 [SQLServerNClob Class](../content/SQLServerNClob-Class.md)  
  
  