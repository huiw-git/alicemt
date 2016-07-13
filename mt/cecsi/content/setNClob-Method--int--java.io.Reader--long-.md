---
title: setNClob Method (int, java.io.Reader, long)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
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
# setNClob Method (int, java.io.Reader, long)
  Sets the designated parameter to the specified Reader object, which is the specified number of characters long.  
  
## Syntax  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 An **int** that indicates the parameter index.  
  
 *reader*  
  
 A Reader object that indicates the parameter value.  
  
 *length*  
  
 An **long** that indicates the number of characters in the parameter value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setNClob method is specified by the setNClob method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [setNClob Method &#40;SQLServerPreparedStatement&#41;](../content/setNClob-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)  
  
  