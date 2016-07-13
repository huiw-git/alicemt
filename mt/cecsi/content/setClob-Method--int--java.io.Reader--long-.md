---
title: setClob Method (int, java.io.Reader, long)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
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
# setClob Method (int, java.io.Reader, long)
  Sets the designated parameter to the specified Reader object, which is the given number of characters long.  
  
## Syntax  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 An **int** that indicates the parameter index.  
  
 *reader*  
  
 A Reader object.  
  
 *length*  
  
 A **long** that indicates the number of characters in the parameter value.  
  
## Remarks  
 This setClob method is specified by the setClob method in the java.sql.PreparedStatement interface.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## See Also  
 [setClob Method &#40;SQLServerPreparedStatement&#41;](../content/setClob-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)  
  
  