---
title: setAsciiStream Method (SQLServerClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerClob.setAsciiStream
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6e1779df-3b2a-41d1-8dca-99692cc9da14
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
# setAsciiStream Method (SQLServerClob)
  Returns a stream to be used to write ASCII characters to the CLOB starting at the given position.  
  
## Syntax  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the CLOB object.  
  
## Return Value  
 The stream to which ASCII encoded characters can be written.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This setAsciiStream method is specified by the setAsciiStream method in the java.sql.Clob interface.  
  
 Character data in the CLOB is overwritten by the output stream starting at the given position and can overrun the initial length of the CLOB. Specifying a position\+1 value will append ASCII characters. Specifying a position\+2 or greater \(or zero or less\) value will cause a position error to be thrown.  
  
## See Also  
 [SQLServerClob Methods](../content/SQLServerClob-Methods.md)   
 [SQLServerClob Members](../content/SQLServerClob-Members.md)   
 [SQLServerClob Class](../content/SQLServerClob-Class.md)  
  
  