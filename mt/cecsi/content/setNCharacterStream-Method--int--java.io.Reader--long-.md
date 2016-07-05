---
title: setNCharacterStream Method (int, java.io.Reader, long)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36396dc9-f109-4da0-bd64-726704046bbf
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
# setNCharacterStream Method (int, java.io.Reader, long)
  Sets the designated parameter to the specified Reader object.  
  
## Syntax  
  
```  
  
public final void setNCharacterStream(int parameterIndex,  
                                                  java.io.Reader value,  
                                                                long length)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 An **int** that indicates the parameter index.  
  
 *value*  
  
 A Reader object that contains the parameter value.  
  
 *length*  
  
 A **long** that indicates the number of characters in the parameter value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setNCharacterStream method is specified by the setNCharacterStream method in the java.sql.PreparedStatement interface.  
  
 This method should be used for **NCHAR**, **NVARCHAR**, **NTEXT**, and **XML** data types.  
  
 If the length of the stream is different than what is specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [setNCharacterStream Method &#40;int, java.io.Reader&#41;](../content/setNCharacterStream-Method--int--java.io.Reader-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [setNCharacterStream Method &#40;SQLServerPreparedStatement&#41;](../content/setNCharacterStream-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)  
  
  