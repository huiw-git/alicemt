---
title: getMaxFieldSize Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getMaxFieldSize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
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
# getMaxFieldSize Method (SQLServerStatement)
  Retrieves the maximum number of bytes that can be returned for character and binary column values in a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object that is produced by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## Return Value  
 An **int** that indicates the maximum number of bytes that a column can contain, or 0 if there is no limit.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMaxFieldSize method is specified by the getMaxFieldSize method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Methods](../content/SQLServerStatement-Methods.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  