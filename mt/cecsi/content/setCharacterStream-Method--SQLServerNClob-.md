---
title: setCharacterStream Method (SQLServerNClob)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
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
# setCharacterStream Method (SQLServerNClob)
  Retrieves a stream to be used to write a stream of Unicode characters to the **NCLOB** value that this **java.sql.NClob** object represents, starting at the specified position.  
  
## Syntax  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the **NCLOB** value; the first position is 1.  
  
## Return Value  
 A Writer object that represents the stream to which Unicode encoded characters can be written.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setCharacterStream method is specified by the setCharacterStream method in the java.sql.NClob interface.  
  
## See Also  
 [SQLServerNClob Methods](../content/SQLServerNClob-Methods.md)   
 [SQLServerNClob Members](../content/SQLServerNClob-Members.md)   
 [SQLServerNClob Class](../content/SQLServerNClob-Class.md)  
  
  