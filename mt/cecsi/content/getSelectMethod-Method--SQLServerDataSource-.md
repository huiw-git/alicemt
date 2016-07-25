---
title: "getSelectMethod Method (SQLServerDataSource)"
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
  - SQLServerDataSource.getSelectMethod
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
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
# getSelectMethod Method (SQLServerDataSource)
  Returns the default cursor type used for all result sets that are created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.  
  
## Syntax  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## Return Value  
 A **String** value that contains the default cursor type.  
  
## Remarks  
 The selectMethod property specifies the default cursor type that is used for a result set. This property is useful when you are dealing with large result sets and do not want to store the entire result set in memory on the client side. By setting the property to "cursor," you can create a server-side cursor that can fetch smaller chunks of data at a time. If the selectMethod property is not set, getSelectMethod returns the default value of "direct".  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  