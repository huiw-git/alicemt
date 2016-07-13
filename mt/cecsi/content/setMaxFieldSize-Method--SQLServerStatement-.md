---
title: setMaxFieldSize Method (SQLServerStatement)
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
  - SQLServerStatement.setMaxFieldSize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
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
# setMaxFieldSize Method (SQLServerStatement)
  Sets the limit for the maximum number of bytes in a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) column storing character or binary values to the given number of bytes.  
  
## Syntax  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### Parameters  
 *max*  
  
 An **int** that indicates the maximum number of bytes.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setMaxFieldSize method is specified by the setMaxFieldSize method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  