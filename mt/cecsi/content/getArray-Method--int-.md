---
title: getArray Method (int)
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
  - SQLServerCallableStatement.getArray (int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 5b839d3f-5a4e-43da-b93c-dc9e0f6d4b3b
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
# getArray Method (int)
  Retrieves the value of the designated parameter as an Array object given the parameter index.  
  
## Syntax  
  
```  
  
public java.sql.Array getArray(int i)  
```  
  
#### Parameters  
 *i*  
  
 An **int** that indicates the parameter index.  
  
## Return Value  
 An Array object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getArray method is specified by the getArray method in the java.sql.CallableStatement interface.  
  
## See Also  
 [getArray Method &#40;SQLServerCallableStatement&#41;](../content/getArray-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  