---
title: updateCharacterStream Method (java.lang.String, java.io.Reader, int)
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
  - SQLServerResultSet.updateCharacterStream (java.lang.String, java.io.Reader, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 08cfc4e0-83f0-4f2f-ac55-b381f34fe67f
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
# updateCharacterStream Method (java.lang.String, java.io.Reader, int)
  Updates the designated column with a character stream value, which will have the specified number of characters.  
  
## Syntax  
  
```  
  
public void updateCharacterStream(java.lang.String columnName,  
                                  java.io.Reader readerValue,  
                                  int length)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
 *readerValue*  
  
 A Reader object.  
  
 *length*  
  
 An **int** that indicates the length of the stream.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This updateCharacterStream method is specified by the updateCharacterStream method in the java.sql.ResultSet interface.  
  
 This method passes Unicode characters from a Reader object to selected text and binary columns. This includes all text columns and **binary**, **varbinary**, **varbinary\(max\)**, **image**, and **xml** columns, but not **udt** columns.  
  
 If the length of the stream is different than that specified in the *length* parameter, the JDBC driver throws an exception when the row is updated or inserted.  
  
 If the length of the stream is unknown, the *length* parameter may be set to \-1 to indicate that the driver should accept the stream regardless of its length. With sqljdbc4.jar, we recommend that you use the JDBC 4.0 method [updateCharacterStream Method &#40;java.lang.String, java.io.Reader&#41;](../content/updateCharacterStream-Method--java.lang.String--java.io.Reader-.md) when the application wants to update the column from a stream whose length is unknown.  
  
## See Also  
 [updateCharacterStream Method &#40;SQLServerResultSet&#41;](../content/updateCharacterStream-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  