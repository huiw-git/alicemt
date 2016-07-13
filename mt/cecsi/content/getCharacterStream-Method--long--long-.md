---
title: getCharacterStream Method (long, long)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
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
# getCharacterStream Method (long, long)
  Returns the **Clob** data as a Reader object or as a stream of characters with the specified position and length.  
  
## Syntax  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### Parameters  
 *pos*  
  
 A **long** that indicates the offset to the first character of the partial value to be retrieved.  
  
 *length*  
  
 A **long** that indicates the length in characters of the partial value to be retrieved.  
  
## Return Value  
 A Reader object that contains the **Clob** data.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getCharacterStream method is specified by the getCharacterStream method in the java.sql.Clob interface.  
  
## See Also  
 [getCharacterStream Method &#40;SQLServerClob&#41;](../content/getCharacterStream-Method--SQLServerClob-.md)   
 [SQLServerClob Methods](../content/SQLServerClob-Methods.md)   
 [SQLServerClob Members](../content/SQLServerClob-Members.md)  
  
  