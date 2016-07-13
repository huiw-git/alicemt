---
title: getString Method (int) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getString (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bfa493c4-fe07-449b-b4d0-384e1a1fce48
manager:jhubbard
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
# getString Method (int) (SQLServerResultSet)
  Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **String** in the Java programming language.  
  
## Syntax  
  
```  
  
public java.lang.String getString(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 An **int** that indicates the column index.  
  
## Return Value  
 A **String** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getString method is specified by the getString method in the java.sql.ResultSet interface.  
  
 All columns in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] can be returned as a String. This means that a **String** representation of all number\-based and character\-based types, and a hex\-string representation of binary columns such as binary, varbinary, varbinary\(max\), image, timestamp, and uniqueidentifier, can be returned.  
  
 Location\-sensitive types such as money, smallmoney, datetime, smalldatetime, float, real, decimal, and numeric will return the canonical toString\(\) format for the underlying value of the type.  
  
 User\-defined types are returned as hexadecimal **String** values.  
  
## See Also  
 [getString Method &#40;SQLServerResultSet&#41;](../content/getString-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  