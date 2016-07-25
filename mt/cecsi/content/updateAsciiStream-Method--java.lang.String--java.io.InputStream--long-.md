---
title: "updateAsciiStream Method (java.lang.String, java.io.InputStream, long)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d426e8b9-62b7-49f8-9863-8697fd3a7085
caps.latest.revision: 19
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
# updateAsciiStream Method (java.lang.String, java.io.InputStream, long)
  Updates the designated column with an ASCII stream value, which will have the specified number of bytes.  
  
## Syntax  
  
```  
  
public void updateAsciiStream(java.lang.String columnName,  
                              java.io.InputStream streamValue,  
                              long length)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
 *streamValue*  
  
 An InputStream object.  
  
 *length*  
  
 The length of the stream.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateAsciiStream method is specified by the updateAsciiStream method in the java.sql.ResultSet interface.  
  
 This method passes ASCII characters (bytes) from an InputStream object to convertible character columns, which are the ASCII range [0x00 – 0x7F] of Unicode, and 874, 932, 936, 949, 950, and 1250 through 1258 code pages. This method performs a conversion to the destination collation page. Trying to update an unconvertible destination column will cause an exception to be thrown. For binary columns, raw bytes are passed.  
  
 If the length of the stream is different than what is specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to -1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [updateAsciiStream Method &#40;java.lang.String, java.io.InputStream&#41;](../content/updateAsciiStream-Method--java.lang.String--java.io.InputStream-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [updateAsciiStream Method &#40;SQLServerResultSet&#41;](../content/updateAsciiStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  