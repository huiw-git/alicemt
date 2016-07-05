---
title: setBinaryStream Method (int, java.io.InputStream, int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setBinaryStream
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: fd6be063-08eb-40cf-9201-5a9f62387726
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
# setBinaryStream Method (int, java.io.InputStream, int)
  Sets the designated parameter to the specified input stream, which will have the specified number of bytes.  
  
## Syntax  
  
```  
  
public final void setBinaryStream(int n,  
                                  java.io.InputStream x,  
                                  int length)  
```  
  
#### Parameters  
 *n*  
  
 An **int** that indicates the parameter number.  
  
 *x*  
  
 An InputStream object.  
  
 *length*  
  
 An **int** that indicates the number of bytes.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setBinaryStream method is specified by the setBinaryStream method in the java.sql.PreparedStatement interface.  
  
 If the length of the stream is different from what is specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [setBinaryStream Method &#40;int, java.io.InputStream&#41;](../content/setBinaryStream-Method--int--java.io.InputStream-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [setBinaryStream Method &#40;SQLServerPreparedStatement&#41;](../content/setBinaryStream-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)  
  
  