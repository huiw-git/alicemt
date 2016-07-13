---
title: getUnicodeStream Method (SQLServerResultSet)
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
  - SQLServerResultSet.getUnicodeStream
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 0dd61865-663b-47e2-b417-e9df418894cc
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
# getUnicodeStream Method (SQLServerResultSet)
  Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a stream of Unicode characters.  
  
> [!NOTE]  
>  This method has been deprecated from the JDBC specification, and calling it will cause a "not implemented" exception to be thrown. Instead, you should use the [getCharacterStream](../content/getCharacterStream-Method--SQLServerResultSet-.md) method.  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[getUnicodeStream Method &#40;int&#41;](../content/getUnicodeStream-Method--int-.md)|Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a stream of Unicode characters.|  
|[getUnicodeStream Method &#40;java.lang.String&#41;](../content/getUnicodeStream-Method--java.lang.String-.md)|Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a stream of Unicode characters.|  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  