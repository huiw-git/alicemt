---
title: setString Method (SQLServerCallableStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.setString
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
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
# setString Method (SQLServerCallableStatement)
  Sets the designated parameter to the given Java **String** value.  
  
## Syntax  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the name of the parameter.  
  
 *s*  
  
 A **String** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setString method is specified by the setString method in the java.sql.CallableStatement interface.  
  
 String to binary conversions are performed only when [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] knows the destination type is binary. In cases where the JDBC driver does not know the underlying type, it will pass the **String** literal and return a server error if the server cannot perform the conversion.  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  