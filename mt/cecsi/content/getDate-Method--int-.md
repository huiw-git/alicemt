---
title: getDate Method (int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getDate (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: aa9f08af-df24-4c80-8298-c4007339b20a
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
# getDate Method (int)
  Retrieves the value of the designated parameter as a java.sql.Date object in the Java programming language given the parameter index.  
  
## Syntax  
  
```  
  
public java.sql.Date getDate(int index)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter index.  
  
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
  
  