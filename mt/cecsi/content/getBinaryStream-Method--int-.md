---
title: getBinaryStream Method (int)
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
  - SQLServerResultSet.getBinaryStream (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
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
# getBinaryStream Method (int)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a binary stream of uninterpreted bytes.  
  
## Syntax  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 An InputStream object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBinaryStream method is specified by the getBinaryStream method in the java.sql.ResultSet interface.  
  
 This method can be used only with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types of binary, varbinary, varbinary\(max\), and image. Trying to use it with other data types will cause an exception to be thrown.  
  
 After this method gets the value as a stream, the value can then be read in chunks from the stream. This method is particularly suitable for retrieving large LONGVARBINARY values.  
  
> [!NOTE]  
>  All the data in the returned stream must be read before getting the value of any other column. The next call to a getter method implicitly closes the stream. Also, a stream can return 0 when the method InputStream.available is called, whether there is data available or not.  
  
## See Also  
 [getBinaryStream Method &#40;SQLServerResultSet&#41;](../content/getBinaryStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  