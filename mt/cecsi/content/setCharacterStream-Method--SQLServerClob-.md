---
title: "setCharacterStream Method (SQLServerClob)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerClob.setCharacterStream
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
caps.latest.revision: 9
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
# setCharacterStream Method (SQLServerClob)
  Returns a stream to be used to write a stream of Unicode characters to the CLOB, starting at the given position.  
  
## Syntax  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the CLOB object.  
  
## Return Value  
 A stream to which Unicode encoded characters can be written.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This setCharacterStream method is specified by the setCharacterStream method in the java.sql.Clob interface.  
  
 Character data in the CLOB is overwritten by the writer starting at the specified position and can over-run the initial length of the CLOB. Specifying a position+1 value will append characters. Specifying a position+2 or greater (or zero or less) value will cause a position error to be thrown.  
  
## See Also  
 [SQLServerClob Methods](../content/SQLServerClob-Methods.md)   
 [SQLServerClob Members](../content/SQLServerClob-Members.md)   
 [SQLServerClob Class](../content/SQLServerClob-Class.md)  
  
  