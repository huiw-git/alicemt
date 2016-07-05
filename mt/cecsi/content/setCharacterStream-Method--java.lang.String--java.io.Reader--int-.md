---
title: setCharacterStream Method (java.lang.String, java.io.Reader, int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.setCharacterStream
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 88a8e89e-8817-4161-85b1-9a9a2fd01cdb
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
# setCharacterStream Method (java.lang.String, java.io.Reader, int)
  Sets the designated parameter to the specifiedReader object, which is the specifiednumber of characters long.  
  
## Syntax  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName,  
                              java.io.Reader value,  
                              int length)  
```  
  
#### Parameters  
 *parameterName*  
  
 A **String** that contains the name of the parameter.  
  
 *value*  
  
 A Reader object that contains the Unicode data.  
  
 *length*  
  
 An **int** that indicates the length in number of characters.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setCharacterStream method is specified by the setCharacterStream method in the java.sql.CallableStatement interface.  
  
 If the length of the stream is different than that specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [setCharacterStream Method \(java.lang.String, java.io.Reader\)](../content/setCharacterStream-Method--java.lang.String--java.io.Reader-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  