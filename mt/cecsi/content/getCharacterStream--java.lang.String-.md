---
title: getCharacterStream (java.lang.String)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getCharacterStream(String paramName)
apilocation: 
  - SQLServerCallableStatement.getCharacterStream(String paramName)
apitype: Assembly
ms.assetid: 5281e1b8-19b8-4fe5-83be-929d1987e25d
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
# getCharacterStream (java.lang.String)
  Retrieves the value of the designated parameter as a java.io.Reader object given the parameter name.  
  
## Syntax  
  
```  
  
public final java.io.Reader getCharacterStream(java.lang.String paramName)  
```  
  
#### Parameters  
 *paramName*  
  
 A **String** that indicates the parameter name.  
  
## Return Value  
 A Reader object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## See Also  
 [getCharacterStream Method &#40;SQLServerCallableStatement&#41;](../content/getCharacterStream-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  