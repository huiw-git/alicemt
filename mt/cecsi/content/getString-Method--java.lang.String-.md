---
title: getString Method (java.lang.String)
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
  - SQLServerCallableStatement.getString (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f67371e0-e879-4188-85fc-ecb85f0be2a9
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
# getString Method (java.lang.String)
  Retrieves the value of the designated parameter as a **String** in the Java programming language given the parameter name.  
  
## Syntax  
  
```  
  
public java.lang.String getString(java.lang.String sCol)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 A **String** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getString method is specified by the getString method in the java.sql.CallableStatement interface.  
  
 All columns in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] can be returned as a string. This means that a string representation of all number\-based and character\-based types, and a hex\-string representation of binary columns such as binary, varbinary, varbinary\(max\), image, timestamp, and uniqueidentifier, can be returned.  
  
 Location\-sensitive types such as money, smallmoney, datetime, smalldatetime, float, real, decimal, and numeric will return the canonical toString\(\) format for the underlying value of the type.  
  
 User\-defined types are returned as hexadecimal string values.  
  
## See Also  
 [getString Method &#40;SQLServerCallableStatement&#41;](../content/getString-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  