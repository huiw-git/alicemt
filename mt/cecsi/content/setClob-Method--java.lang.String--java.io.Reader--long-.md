---
title: setClob Method (java.lang.String, java.io.Reader, long)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc9fddea-134e-4440-ba54-a1f74bb40c46
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
# setClob Method (java.lang.String, java.io.Reader, long)
  Sets the designated parameter to the specified Reader object, which is the specified number of characters long.  
  
## Syntax  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.io.Reader value,  
            long length)  
```  
  
#### Parameters  
 *parameterName*  
  
 A **String** that contains the parameter name.  
  
 *value*  
  
 A Reader object.  
  
 *length*  
  
 A **long** that indicates the number of characters in the stream.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setClob method is specified by the setClob method in the java.sql.CallableStatement interface.  
  
## See Also  
 [setClob Method &#40;SQLServerCallableStatement&#41;](../content/setClob-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)  
  
  