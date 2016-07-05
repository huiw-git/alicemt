---
title: getDate Method (java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getDate (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a605bca6-d960-4756-ad14-0f42b313e60a
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
# getDate Method (java.lang.String)
  Retrieves the value of the designated parameter as a java.sql.Date object in the Java programming language given the parameter name.  
  
## Syntax  
  
```  
  
public java.sql.Date getDate(java.lang.String sCol)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
## Return Value  
 A Date object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getDate method is specified by the getDate method in the java.sql.CallableStatement interface.  
  
 This method returns a valid date part of a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **datetime** or **smalldatetime** data type, with the time part set to the Java time baseline of 00:00 \(midnight\).  
  
## See Also  
 [getDate Method &#40;SQLServerCallableStatement&#41;](../content/getDate-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  