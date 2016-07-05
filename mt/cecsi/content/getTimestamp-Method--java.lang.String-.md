---
title: getTimestamp Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getTimestamp (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4d5174db-365c-4476-9472-7871578ef34c
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
# getTimestamp Method (java.lang.String)
  Retrieves the value of the designated parameter as a java.sql.Timestamp object in the Java programming language given the parameter name.  
  
## Syntax  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String sCol)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 A Timestamp object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTimestamp method is specified by the getTimestamp method in the java.sql.CallableStatement interface.  
  
 This method returns values only from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **datetime** and **smalldatetime** columns.  
  
## See Also  
 [getTimestamp Method &#40;SQLServerCallableStatement&#41;](../content/getTimestamp-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  