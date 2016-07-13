---
title: setSelectMethod Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setSelectMethod
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
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
# setSelectMethod Method (SQLServerDataSource)
  Sets the default cursor type that is used for all result sets that are created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.  
  
## Syntax  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### Parameters  
 *selectMethod*  
  
 A **String** value that contains the default cursor type.  
  
## Remarks  
 The selectMethod is the default cursor type that is used for a result set. This property is useful when you are dealing with large result sets and do not want to store the whole result set in memory on the client side. By setting the property to "cursor," you can create a server\-side cursor that can fetch smaller chunks of data at a time. If the selectMethod property is not set, [getSelectMethod](../content/getSelectMethod-Method--SQLServerDataSource-.md) returns the default value of "direct".  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  