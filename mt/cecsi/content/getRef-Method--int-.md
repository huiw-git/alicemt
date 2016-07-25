---
title: "getRef Method (int)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.getRef (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 905dd02a-0c7f-475b-8be4-341b4359c766
caps.latest.revision: 9
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
# getRef Method (int)
  Retrieves the value of the designated parameter as a Ref object in the Java programming language given the parameter index.  
  
## Syntax  
  
```  
  
public java.sql.Ref getRef(int i)  
```  
  
#### Parameters  
 *i*  
  
 An **int** that indicates the parameter index.  
  
## Return Value  
 A Ref object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getRef method is specified by the getRef method in the java.sql.CallableStatement interface.  
  
## See Also  
 [getRef Method &#40;SQLServerCallableStatement&#41;](../content/getRef-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  