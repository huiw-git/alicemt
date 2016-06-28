---
title: getBinaryStream Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
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
# getBinaryStream Method (java.lang.String)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a binary stream of uninterpreted bytes.  
  
## Syntax  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
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
  
  