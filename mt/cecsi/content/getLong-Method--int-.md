---
title: getLong Method (int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getLong (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b7078ca7-fd2a-4474-ab29-989ae28c77e8
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
# getLong Method (int)
  Retrieves the value of the designated parameter as a **long** in the Java programming language given the parameter index.  
  
## Syntax  
  
```  
  
public long getLong(int index)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter index.  
  
## Return Value  
 A **long** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getLong method is specified by the getLong method in the java.sql.CallableStatement interface.  
  
 This method is supported only on [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types that can safely return an integer value such as bigint, int, smallint, tinyint, and bit. Using this method on any other data types will cause an exception to be thrown.  
  
## See Also  
 [getLong Method &#40;SQLServerCallableStatement&#41;](../content/getLong-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  