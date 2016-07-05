---
title: setString Method (long, java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerClob.setString (long, java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 1b2190e9-5ace-497a-8554-0e913ea9b0cb
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
# setString Method (long, java.lang.String)
  Writes the given **String** to the CLOB starting at the given position.  
  
## Syntax  
  
```  
  
public int setString(long pos,  
                     java.lang.String s)  
```  
  
#### Parameters  
 *pos*  
  
 The position at which to start writing to the CLOB.  
  
 *s*  
  
 The **String** to be written to the CLOB.  
  
## Return Value  
 The number of characters written.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This setString method is specified by the setString method in the java.sql.Clob interface.  
  
 Character data is overwritten starting at the specified position and can over\-run the initial length of the CLOB. Specifying a position\+1 value will append the string. Specifying a position\+2 or greater \(or zero or less\) values will cause a position error to be thrown.  
  
## See Also  
 [setString Method &#40;SQLServerClob&#41;](../content/setString-Method--SQLServerClob-.md)   
 [SQLServerClob Methods](../content/SQLServerClob-Methods.md)   
 [SQLServerClob Members](../content/SQLServerClob-Members.md)   
 [SQLServerClob Class](../content/SQLServerClob-Class.md)  
  
  