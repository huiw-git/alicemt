---
title: updateBinaryStream Method (int, java.io.InputStream, long)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f84cfbe6-ebab-4357-8770-f1db34ecb04f
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
# updateBinaryStream Method (int, java.io.InputStream, long)
  Updates the designated column with a binary stream value, which will have the specified number of bytes.  
  
## Syntax  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
 *x*  
  
 An InputStream object.  
  
 *length*  
  
 A **long** that indicates the length of the stream.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateBinaryStream method is specified by the updateBinaryStream method in the java.sql.ResultSet interface.  
  
 This method passes bytes from an InputStream object to selected [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] binary columns such as binary, varbinary, varbinary\(max\), image, xml, and udt. Updating character columns is not supported with this method. To update character columns with an InputStream, use the [updateAsciiStream](../content/updateAsciiStream-Method--SQLServerResultSet-.md) method.  
  
 If the length of the stream is different than what is specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [updateBinaryStream Method &#40;int, java.io.InputStream&#41;](../content/updateBinaryStream-Method--int--java.io.InputStream-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [updateBinaryStream Method &#40;SQLServerResultSet&#41;](../content/updateBinaryStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  