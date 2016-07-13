---
title: getBytes Method (java.lang.String) (SQLServerResultSet)
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
  - SQLServerResultSet.getBytes (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ff617165-47f8-41c1-9c51-37ffc7714923
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
# getBytes Method (java.lang.String) (SQLServerResultSet)
  Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** array in the Java programming language.  
  
## Syntax  
  
```  
  
public byte[] getBytes(java.lang.String columnName)  
```  
  
#### Parameters  
 *columnName*  
  
 A **String** that contains the column name.  
  
## Return Value  
 An array of **byte** values.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBytes method is specified by the getBytes method in the java.sql.ResultSet interface.  
  
 This method supports retrieving all columns as a raw read of bytes from the server. It returns an array of bytes directly from the server, in the format that is stored on the server.  
  
 In a previous version of the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerResultSet.getBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
## See Also  
 [getBytes Method &#40;SQLServerResultSet&#41;](../content/getBytes-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  