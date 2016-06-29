---
title: setCharacterStream Method (java.lang.String, java.io.Reader, long)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54fb2f13-f8d8-47b5-bec1-4a5af3e86a84
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
# setCharacterStream Method (java.lang.String, java.io.Reader, long)
  Sets the designated parameter to the specified java.io.Reader object, which is the specified number of characters long.  
  
## Syntax  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### Parameters  
 *parameterName*  
  
 A **String** that contains the parameter name.  
  
 *reader*  
  
 A Reader object that contains the Unicode data.  
  
 *length*  
  
 A **long** that indicates the number of characters in the stream.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setCharacterStream method is specified by the setCharacterStream method in the java.sql.CallableStatement interface.  
  
 If the length of the stream is different than what is specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [setCharacterStream Method \(java.lang.String, java.io.Reader\)](../content/setCharacterStream-Method--java.lang.String--java.io.Reader-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [setCharacterStream Method &#40;SQLServerCallableStatement&#41;](../content/setCharacterStream-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)  
  
  